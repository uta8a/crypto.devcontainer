ARG VARIANT=3-bullseye
FROM mcr.microsoft.com/vscode/devcontainers/python:${VARIANT}

# [Choice] Node.js version: none, lts/*, 16, 14, 12, 10
ARG NODE_VERSION="none"
RUN if [ "${NODE_VERSION}" != "none" ]; then su vscode -c "umask 0002 && . /usr/local/share/nvm/nvm.sh && nvm install ${NODE_VERSION} 2>&1"; fi

RUN apt -qq update \
    && apt -qq install -y --no-install-recommends \
    netcat \
    tmux \
    vim \
    sagemath \
    openssl \
    wget \
    pari-gp \
    python3-cypari2 \
    python3-cysignals-pari \
    p7zip-full \
    && rm -rf /var/lib/apt/lists/*

RUN wget https://hashcat.net/files/hashcat-6.2.4.7z -O /tmp/hashcat.7z
RUN 7z x /tmp/hashcat.7z
RUN cp /hashcat-6.2.4/hashcat.bin /usr/local/bin/hashcat

RUN pip3 install --no-cache-dir \
    pwntools \
    pycryptodome \
    z3-solver
