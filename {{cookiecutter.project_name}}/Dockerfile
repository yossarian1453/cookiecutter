FROM python:{{cookiecutter.python_version}}-slim

# Install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

{%- if cookiecutter.include_r == "yes" %}
# Install R
RUN apt-get update && apt-get install -y --no-install-recommends \
    r-base r-base-dev \
    && rm -rf /var/lib/apt/lists/*
{%- endif %}

WORKDIR /workspace
COPY pyproject.toml ./
RUN uv sync --no-install-project || true

CMD ["bash"]