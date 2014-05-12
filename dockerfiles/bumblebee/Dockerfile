FROM ubuntu:precise

RUN apt-get update
RUN apt-get install -y python-software-properties software-properties-common git supervisor bzip2 language-pack-en-base
RUN update-locale LC_ALL=en_US.UTF-8
ENV LC_ALL en_US.UTF-8
RUN add-apt-repository ppa:chris-lea/node.js
RUN apt-get update && apt-get install -y nodejs

RUN git clone https://github.com/adsabs/bumblebee /bumblebee
ADD local-config.json /bumblebee/
RUN npm install -g grunt-cli
RUN cd bumblebee && npm install && grunt setup

EXPOSE 80

#Supervisord will take care of keeping services up
ADD supervisord.conf /etc/supervisor/supervisord.conf
CMD ["/usr/bin/supervisord"]