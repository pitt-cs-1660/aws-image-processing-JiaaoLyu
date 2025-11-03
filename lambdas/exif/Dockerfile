FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# Copy dependency config
COPY pyproject.toml .

# Install dependencies
RUN uv pip install --system pillow boto3

# Copy handler code
COPY handler.py ${LAMBDA_TASK_ROOT}

# Set python path
ENV PYTHONPATH="${LAMBDA_TASK_ROOT}"

# Lambda start command
CMD ["handler.exif_handler"]
