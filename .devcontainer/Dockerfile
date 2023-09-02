FROM debian:bookworm

ARG USERNAME=scotthal
ARG USER_UID=1100
ARG USER_GID=$USER_UID

ENV DEBAIN_FRONTEND=noninteractive

RUN groupadd --gid $USER_GID $USERNAME; \
  useradd -s /bin/bash --uid $USER_UID --gid $USER_GID -m $USERNAME; \
  echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME; \
  chmod 440 /etc/sudoers.d/$USERNAME; \
  apt-get update; \
  apt-get -y dist-upgrade; \
  apt-get -y install locales less dialog apt-utils man-db bc zsh fish zip unzip sudo tmux bat vim emacs-nox git iproute2 procps lsb-release libnss3-tools curl httpie jq sqlite3 docker.io docker-compose; \
  apt-get -y install build-essential autoconf automake cmake m4 bison flex gettext; \
  apt-get -y install libssl-dev libcurl4-openssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libncurses5-dev libncursesw5-dev libelf-dev xz-utils tk-dev libffi-dev liblzma-dev; \
  apt-get -y install libgmp-dev; \
  echo 'en_US.UTF-8 UTF-8' >> /etc/locale.gen; \
  locale-gen; \
  update-locale LANG=en_US.UTF-8; \
  usermod -s /bin/zsh $USERNAME; \
  usermod -a -G docker $USERNAME; \
  apt-get autoremove -y; \
  apt-get clean -y; \
  rm -rf /var/lib/apt/lists/*

ENV DEBAIN_FRONTEND=

USER ${USERNAME}

CMD ["/bin/zsh", "-l"]
