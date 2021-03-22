### BASE ###
FROM alpine:3.12 as zosbin
ARG ARCH

RUN apk --no-cache add alpine-sdk fuse3-dev hiredis-dev linux-headers curl

RUN git clone https://github.com/threefoldtech/0-db-fs && \
  cd 0-db-fs && \
  make release

RUN git clone https://github.com/threefoldtech/0-db && \
  cd 0-db/libzdb && \
  make release && \
  cd ../zdbd && \
  make release

RUN mkdir 0-stor_v2 && \
  curl -L https://github.com/threefoldtech/0-stor_v2/releases/download/v0.2.0/zstor_v2-x86_64-linux-musl -o /0-stor_v2/zstor && \
  chmod +x /0-stor_v2/zstor && \
  curl -L https://github.com/threefoldtech/0-stor_v2/releases/download/v0.2.0/zstor_monitor-x86_64-linux-musl -o /0-stor_v2/monitor && \
  chmod +x /0-stor_v2/monitor
