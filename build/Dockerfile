FROM ubuntu:latest

ENV PAPERMC_URL="https://api.papermc.io/v2/projects/paper/versions/1.19.2/builds/130/downloads/paper-1.19.2-130.jar"

WORKDIR /opt

RUN apt update && \
    apt install -y openjdk-17-jdk wget

RUN wget ${PAPERMC_URL} -O paper.jar

RUN mkdir mc

RUN echo '#!/bin/env bash\necho "eula=true" > /opt/eula.txt\njava -Xms2G -Xmx2G -jar /opt/mc/paper.jar --nogui' > start.sh && \
    chmod 700 start.sh

WORKDIR /opt/mc
ENTRYPOINT [ "/opt/start.sh" ]