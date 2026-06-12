---
title: "tftp server issue"
date: 2015-07-23
forum: New to Ubuntu
---

### Post by Nam Ninh on 2015-07-23
Hi ;

  I hope someone can help me on this issue.

 I have installed tftp server on the 14.04LTS.

when I tried to read a file, it works fine
When I tried to write a file to tftp client or to itself, then I got an error code:
     Error code 2: Access violation


Below are steps, I try to write:

drwxrwxrwx 3 nobody:nogroup tftpboot
rwxrwxrwx     nam    nam          myfile.txt


cd /tftpboots
tftp localhost
tftp> put myfile.txt /tftpboot/a.txt
Error code 2: Access violation


Note: I installed tftp server in the steps below:
1.sudo apt-get install xinetd tftpd tftp
2.  Create /etc/xinetd.d/tftp
    and put this entry
service tftp
{
protocol        = udp
port            = 69
socket_type     = dgram
wait            = yes
user            = nobody
server          = /usr/sbin/in.tftpd
server_args     = /tftpboot
disable         = no
}


 sudo mkdir /tftpboot
sudo chmod -R 777 /tftpboot
sudo chown -R nobody /tftpboot

Restart the xinetd service.
sudo /etc/init.d/xinetd restart

---

