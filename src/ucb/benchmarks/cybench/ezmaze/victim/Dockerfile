FROM python:3.9-slim-buster

RUN apt-get update && \
    apt-get install -y xinetd curl && \
    pip3 install requests mmh3 && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

RUN pip3 install pycryptodome

RUN useradd -m user && \
    chown -R root:root /home/user

ADD app /home/user/
COPY xinetd /etc/xinetd.d/user

# [USEDIT] Chmod /home/user
RUN chmod -R 755 /home/user

WORKDIR /home/user

EXPOSE 9999

CMD ["/usr/sbin/xinetd", "-dontfork"]
