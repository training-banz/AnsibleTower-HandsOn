##################################################
#                                                #
# Creates a base rhel7  image with OpenSSH       #
#                                                #
##################################################
FROM            rhel7:latest
MAINTAINER      Masatoshi Murai

# Install
RUN yum install -y openssh-server && yum clean all
RUN yum update -y && yum clean all
RUN systemctl enable sshd

# Setup sshd
ADD authorized_keys /root/.ssh/authorized_keys
RUN chmod 600  /root/.ssh/authorized_keys
RUN sed -ri 's/^#PermitRootLogin yes/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/^#RSAAuthentication yes/RSAAuthentication yes/' /etc/ssh/sshd_config
RUN sed -ri 's/^#PasswordAuthentication yes/PasswordAuthentication no/' /etc/ssh/sshd_config
