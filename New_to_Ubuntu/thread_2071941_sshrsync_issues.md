---
title: "ssh/rsync issues"
date: 2012-10-16
forum: New to Ubuntu
---

### Post by djyoung4 on 2012-10-16
So i recently updated my server from 10.04 to 12.04.  I had a script that I used to backup and sync my music from my laptop to the server
```
#!/bin/sh
LOCALDIR=/home/djyoung4/Music/
REMOTEDIR=/mnt/Storage1/Music/
SERVER=192.168.1.102
echo Syncing with $SERVER
echo Sending...
rsync --rsh=ssh -aizuKL $LOCALDIR home@$SERVER:$REMOTEDIR
echo Fetching...
rsync --rsh=ssh -aizuKL home@$SERVER:$REMOTEDIR $LOCALDIR 
notify-send sync done
exit
```
with the update to 12.04 I cannot get the script to work correctly.  I keep getting a connection refused port 22 closed
```
[djyoung4@archbang Documents]$ sh Musicsync.sh
Syncing with 192.168.1.102
Sending...
ssh: connect to host 192.168.1.102 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(605) [sender=3.0.9]
Fetching...
ssh: connect to host 192.168.1.102 port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code 255) at io.c(605) [Receiver=3.0.9]
```
rsync and openssh are installed on both machines and googling has turned up nothing so far.  any ideas?
I can vnc into the box no problem

---

### Post by papibe on 2012-10-16
Hi djyoung4.

Let's try to make sure your ssh connection is working OK.

Could you post the result of an ssh connection using the triple verbose option?
```
ssh -vvv 192.168.1.102
```
Regards.

---

### Post by djyoung4 on 2012-10-16
```
[djyoung4@archbang Documents]$ sudo ssh -vvv server@192.168.1.102
OpenSSH_6.1p1, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to 192.168.1.102 [192.168.1.102] port 22.
debug1: connect to address 192.168.1.102 port 22: Connection refused
ssh: connect to host 192.168.1.102 port 22: Connection refused

```

---

### Post by papibe on 2012-10-16
Thanks.

It look like the ssh service is not running, or set to use another port.

Could you post the results of these commands on the server?
```
apt-cache policy openssh-server 

sudo service ssh status

grep -i port /etc/ssh/sshd_config
```
Regards.

---

### Post by djyoung4 on 2012-10-16
```
server@server-home:~$ apt-cache policy openssh-server
openssh-server:
  Installed: (none)
  Candidate: 1:5.9p1-5ubuntu1
  Version table:
     1:5.9p1-5ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
server@server-home:~$ sudo service ssh status
[sudo] password for server: 
ssh: unrecognized service
server@server-home:~$ grep -i port /etc/ssh/sshd_config
grep: /etc/ssh/sshd_config: No such file or directory

```
ha seems to be my problem

---

### Post by papibe on 2012-10-16
Thanks.

The server side of the openssh package has not been installed yet on the server.

Install it like this:
```
sudo apt-get install openssh-server
```
Let us know how it goes.
Regards.

---

### Post by djyoung4 on 2012-10-16
```
[djyoung4@archbang Documents]$ sh Musicsync.sh
Syncing with 192.168.1.102
Sending...
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
a0:7c:46:25:f5:42:c8:d7:f0:80:e4:5b:2b:a2:82:06.
Please contact your system administrator.
Add correct host key in /home/djyoung4/.ssh/known_hosts to get rid of this message.
Offending RSA key in /home/djyoung4/.ssh/known_hosts:2
RSA host key for 192.168.1.102 has changed and you have requested strict checking.
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(605) [sender=3.0.9]
Fetching...
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
a0:7c:46:25:f5:42:c8:d7:f0:80:e4:5b:2b:a2:82:06.
Please contact your system administrator.
Add correct host key in /home/djyoung4/.ssh/known_hosts to get rid of this message.
Offending RSA key in /home/djyoung4/.ssh/known_hosts:2
RSA host key for 192.168.1.102 has changed and you have requested strict checking.
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [Receiver]
rsync error: unexplained error (code 255) at io.c(605) [Receiver=3.0.9]

```I cant seem to figure out where to add the new RSA key.  Hopefully someone isn't really doing something nasty.  
edit:  I added it in the file and ran the script and still no luck.  just gave me some other errors and then closed the terminal before I could copy them

---

### Post by papibe on 2012-10-16
Either remove the second line of your ~/.ssh/know_hosts, or just remove the file (if you don't ssh to other machines).

Try again, and let us know how it goes.
Regards.

---

### Post by drmrgd on 2012-10-16
I think you're getting that because your system is recognizing that the server has changed and now has a different key.  If purge the server's entry from ~/.ssh/known_hosts you should be OK again.  

If you can't decipher which is the server's (which is not unlikely!) I think you can just purge the whole file.  The only downside side that I've seen is that you just have to say "yes" to add a key when connecting to a server that you've connected to before.  You can test by just backing the file up before you delete it (just changing the name is enough).

---

### Post by drmrgd on 2012-10-16
> **papibe said:**
> Either remove the second line of your ~/.ssh/know_hosts, or just remove the file (if you don't ssh to other machines).

Try again, and let us know how it goes.
Regards.

Not only beat me to it...but taught me something in the process!  Now I know where to look for the offending key in the file.  I usually just purge the whole file, which is not a big deal, but a bit of a pain since I connect to a bunch of different servers.  Thanks!

---

### Post by djyoung4 on 2012-10-16
I deleted the whole file and retried but got the same error.  My ip's are not static so I am adding new ones all the time.  Ill try reinstalling openssh on the laptop
edit: same problem after reinstalling
If I try sshing from the server into my laptop I get a port22: connection refused as well

---

### Post by papibe on 2012-10-16
Let's tackle one direction at a time.

Do this on the laptop:
```
rm -rf ~/.ssh
```
Then, try to connect to the server again.

Regards.

BTW: do not re-install openssh again, as it will create another server key and you'll face the same ugly message.

---

### Post by djyoung4 on 2012-10-16
still get the same error as before.
```
[djyoung4@archbang ~]$ sudo ssh server@192.168.1.102
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that a host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
a0:7c:46:25:f5:42:c8:d7:f0:80:e4:5b:2b:a2:82:06.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending RSA key in /root/.ssh/known_hosts:1
RSA host key for 192.168.1.102 has changed and you have requested strict checking.
Host key verification failed.

```

---

### Post by drmrgd on 2012-10-16
Just to be sure, you should be modifying the known_hosts file on the client computer, not on the server computer.  I might be misreading, but it seems you're modifying this on the server side.

---

### Post by papibe on 2012-10-16
This is different, as you are trying to connect using root (then /root/.ssh is being looked).

Could you try using your regular user, and make sure your regular user ~/.ssh has been remove.

Let us know how it goes.
Regards.

---

### Post by djyoung4 on 2012-10-16
=D>=D>=D>=D>=D>=D>=D>
```
[djyoung4@archbang ~]$ ssh server@192.168.1.102
The authenticity of host '192.168.1.102 (192.168.1.102)' can't be established.
ECDSA key fingerprint is 02:b8:05:f1:62:fc:57:78:ce:28:e4:f5:ca:45:60:31.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '192.168.1.102' (ECDSA) to the list of known hosts.
server@192.168.1.102's password: 
Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-32-generic x86_64)

 * Documentation:  https://help.ubuntu.com/

*** /dev/sdb2 will be checked for errors at next reboot ***

server@server-home:~$ 

```
The only reason I was using sudo was because my music files are stored in /mnt/ which seems to require sudo in order to make any changes to the directories.  Fix one problem and you get another.  I thank you for the help gentlemen

---

### Post by papibe on 2012-10-16
> **djyoung4 said:**
> The only reason I was using sudo was because my music files are stored in /mnt/ which seems to require sudo in order to make any changes to the directories.

It would be safest to grant access to the server's instance of your regular user.

For instance, on the server:
```
sudo chown -R server:server /mnt/Storage1/Music/
sudo chmod -R u+rw /mnt/Storage1/Music/
```
being 'server' the regular user on the machine that we've called server.

Let us know how it goes.
Regards.

---

### Post by djyoung4 on 2012-10-16
for the first one I just get a bunch of operation not permitted for each folder in /mnt/Storage1/Music.  The second one seemed to work.

---

### Post by papibe on 2012-10-16
What kind of disk is it?

Internal, external, ext4, ntfs?

Regards.

---

### Post by djyoung4 on 2012-10-16
internal fat hard disk.  Western Digital 1 TB green

---

### Post by papibe on 2012-10-16
OK.

The only way to set the proper ownership and permissions on a FAT filesystem is in the mount options.

Make sure you mount the disk so that the regular user has both ownership and permissions on it.

If you need help with that, please post your mounting table (/etc/fstab)

Regards.

---

