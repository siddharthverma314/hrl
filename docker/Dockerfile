FROM nvidia/cuda:10.1-base

# install dependencies
RUN apt-get update && apt-get install -y \
	build-essential \
	curl \
	git \
	wget \
	unzip
        

# install stack
RUN curl -sSL https://get.haskellstack.org/ | sh

# set workdir
WORKDIR /app

# install hasktorch
RUN cd /app && git clone https://github.com/hasktorch/hasktorch.git
RUN cd /app/hasktorch/deps && ./get-deps.sh -a cu101
RUN cd /app/hasktorch && source setenv && stack build
