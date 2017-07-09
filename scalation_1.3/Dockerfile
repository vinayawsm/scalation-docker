FROM ubuntu:16.04

# installing java
RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y  software-properties-common && \
    add-apt-repository ppa:webupd8team/java -y && \
    apt-get update && \
    echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | /usr/bin/debconf-set-selections && \
    apt-get install -y oracle-java8-installer && \
    apt-get clean

# installing scala
RUN apt-get remove scala-library scala && \
	wget http://www.scala-lang.org/files/archive/scala-2.12.2.deb && \
	dpkg -i scala-2.12.2.deb && \
	apt-get update && \
	apt-get install -y scala && \
	apt-get clean

# installing sbt
RUN apt-get install apt-transport-https && \
	echo "deb https://dl.bintray.com/sbt/debian /" | tee -a /etc/apt/sources.list.d/sbt.list && \
	apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 2EE0EA64E40A89B84B2DF73499E82A75642AC823 && \
	apt-get update && \
	apt-get install -y sbt && \
	apt-get clean

# downloading scalation
RUN wget http://cobweb.cs.uga.edu/~jam/scalation_1.3.tar.gz && \
	tar xvfz scalation_1.3.tar.gz -C /root/

WORKDIR /root/scalation_1.3

CMD ["/bin/bash"]
