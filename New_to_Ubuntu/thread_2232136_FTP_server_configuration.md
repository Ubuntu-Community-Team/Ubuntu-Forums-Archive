---
title: "FTP server configuration"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by vangend.robert on 2014-06-30
Hello all,
I have a small business and for the past 2-3 years I have been able to give my customers access to upload / download data via ftp. 

The server is / was a Debian Squeeze machine.

On my side of the router I have several windows 7 machines, a data server (Ubuntu 12.04) and of course the ftp server.

A couple of weeks ago we started experiencing some internet connection issues. I eventually discovered that when we had this problem, I was not able to ping the router, or I would regularly lose packets running “ping xx.xx.xx.xx –t” from any machine.

At one point I did something that made me believe that there was an internal IP conflict (I don’t recall what it was that I did). To correct the problem I started switching off various machines and devices, and to cut a long story short, I discovered that when the FTP server was off, the problem would consistently go away.

I also had some internal network issues, where from time to time my windows machines would no longer see the data server. This issue also seems to have disappeared now that the FTP server is off.

Last week the FTP server would not work anymore (no upload download possible). Even SSH’ing into the machine had a new problem. This problem was that even as “sudo” I could not change directory into the individual customer directories. I was getting a “permission denied” error when trying to cd into a directory.

Anyway, there are clearly problems. Usually I do all my own Linux server set-up stuff, but when I tried to set-up the Debian FTP server, I just could not get it right, and could not afford to spend any more time. Eventually I hired an outside contractor to get the FTP working on my Debian machine.

The problem with this is, that if we have problems, I need to get an outside contractor to come and fix the problem again. I don’t mind paying for the service (as long as the cost is reasonable of course), but I really cannot afford to wait a few days for someone to come and look at the problem.

Therefore, I would like to take a shot at setting up a FTP server on a completely new machine running on Ubuntu 12.04 like the data server. I am not sure what happened to the Debian machine, but clearly there are some major problems. Therefore, yesterday, I took an old box and installed Ubuntu 12.04. I have also install vsftpd, and followed a step by step guide to configure. I am having some problems however.

Here is a quick summary of some of the things I have done so far:
1.)    Installed Ubuntu server 12.04
2.)    Installed vsftpd
3.)    Installed samba server (I need to copy data from my local windows machines to the ftp server).
4.)    Setup a user called “ftpuser” and of course create a home directory and password for the user.

Right now I am not able to connect to the ftp server using FileZilla from one of the W7 machines. This is the error is get:
“Connecting to 10.0.0.202:21... Status:   Connection attempt failed with "ECONNREFUSED - Connection refused by server".”

I have been through quite a few forum posts and have tried to mess around with a few settings. What troubles me the most however, is that when I start the vsftpd service everything looks fine and the terminal returns a process id. When I try to stop the service though, it looks as though it is not running.
 
Example:
administrator@ubuntu:~$ sudo service vsftpd start
vsftpd start/running, process 25266
 
administrator@ubuntu:~$ sudo service vsftpd stop
stop: Unknown instance:
 
Here is the current vsftpd.conf
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Banner.
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
allow_writable_chroot=YES
pasv_enable=Yes
spasv_max_port=30000
pasv_min_port=30100
 
Here is some output from various things I have tried:
---------------
sudo netstat –ltn
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN
tcp6       0      0 :::22                   :::*                    LISTEN
---------------
sudo service vsftpd status
vsftpd stop/waiting
---------------
dpkg -l | grep -i "ftp"
ii  curl                              7.22.0-3ubuntu4.8            Get a file from an HTTP, HTTPS or FTP server
ii  ftp                               0.17-25                      classical file transfer client
ii  vsftpd                            2.3.5-1ubuntu2               lightweight, efficient FTP server written for security
---------------
 
If anyone has any advice, I would be very happy if you would share.
 
Or if anyone has any suggestions on alternatives to using FTP (I know this is not secure). I don’t want to use any cloud based solutions, since keeping the data upload and download information on my own internal servers is important to me.
 
Regards
Rob

---

