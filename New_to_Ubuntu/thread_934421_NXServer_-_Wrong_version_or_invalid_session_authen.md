---
title: "NXServer - Wrong version or invalid session authentication cookie"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by cwmoser on 2008-09-30
I've been using NXServer for some time and suddenly get this error
when I try to connect to my Ubuntu PC:

Info: Proxy running in client mode with pid '768'
Session:  Starting session at ....
Error:  The remote NX proxy closed the connection.
Error: Failure negotiating the session in stage '7'
Error: Wrong version or invalid session authentication cookie
Session:  Terminating session at ....
Session:  Session terminated at ....

Like I stated, this has been working for some time.
I get this same error if I use a Linux or a Windows PC to remote to my Ubuntu PC.

Any help is appreciated.

Carl

---

### Post by cwmoser on 2008-10-02
I think there are dependencies other than SSH and NXServer that are affecting this.  I've removed and reinstalled both NXServer and ssh several times and I have notes from the time when I did have this working.  Could it be the recent "fix" to the SSH Linux update?

My errors currently are:

$ sudo /usr/NX/bin/nxserver --useradd cwmoser --system
NX> 309 User: cwmoser is already present on the system.
NX> 801 User: cwmoser uses SSHD authentication.
NX> 900 Adding public key for user: cwmoser to the authorized keys file.
NX> 910 WARNING: The SSH key to be used for user authentication could
NX> 910 WARNING: not be added to the private authorized keys file of user.
NX> 910 WARNING: Please note that, with these settings, the user won't be
NX> 910 WARNING: able to successfully run any sessions.
NX> 910 WARNING: Run the following command to get some hints on the possible
NX> 910 WARNING: reasons of the problem:
NX> 910 WARNING:
NX> 910 WARNING: nxserver --usercheck cwmoser
NX> 910 WARNING:
NX> 301 User: cwmoser enabled in the NX user DB.
NX> 999 Bye.

$

---

### Post by cwmoser on 2008-10-02
SOLVED -- I figured it out.  It had to do with ssh key generation and permissions.  Here are my notes:


ssh  -V
ssh  -vX  user1@yourhostname  xterm

chmod  go-w  ~/
mkdir  ~/.ssh
chmod  700  ~/.ssh
ssh-keygen  -q  -f  ~/.ssh/id_rsa  -t  rsa
chmod  go-rwx  ~/.ssh/*


On the Server, put the Public Key in /usr/NX/home/nx/.ssh/authorized_keys2:
	cat  id_rsa.pub  >>  /usr/NX/home/nx/.ssh/authorized_keys2


On the Client, put the Public and Private keys in /home/<user>/.ssh:
	id_rsa
	id_rsa.pub


/etc/ssh/sshd_config file critical items:
Port 22
StrictModes yes

AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

AllowUsers user1 user2 nx


RSAAuthentication yes

PubkeyAuthentication yes

PasswordAuthentication yes





These permissions are critical:
# pwd

/usr/NX/home/nx/.ssh

# ls -l

total 20

-rw-r--r-- 2 nx   root    2736 2008-10-02 19:25 authorized_keys2

-rw-r--r-- 2 nx   root    2736 2008-10-02 19:25 default.id_dsa.pub

-rw------- 1 root root    1675 2008-10-02 19:24 id_rsa

-rw-r--r-- 1 nx   nogroup  782 2008-10-02 19:20 known_hosts

-rw-r--r-- 1 root root    1061 2008-10-02 19:12 SAVEauthorized_keys2

# 



Hope this helps others who have lost NXServer.

NXServer really is great when its working but it can be a bear to fix.

Carl

---

### Post by Mets on 2010-04-20
I had the same error, and I tried what this person suggested, and it's foobar'd my nxserver.  All I'm getting now is "the NX service is unavailable or the NX access was disabled."  How do I undo this?

> **cwmoser said:**
> SOLVED -- I figured it out.  It had to do with ssh key generation and permissions.  Here are my notes:


ssh  -V
ssh  -vX  user1@yourhostname  xterm

chmod  go-w  ~/
mkdir  ~/.ssh
chmod  700  ~/.ssh
ssh-keygen  -q  -f  ~/.ssh/id_rsa  -t  rsa
chmod  go-rwx  ~/.ssh/*


On the Server, put the Public Key in /usr/NX/home/nx/.ssh/authorized_keys2:
	cat  id_rsa.pub  >>  /usr/NX/home/nx/.ssh/authorized_keys2


On the Client, put the Public and Private keys in /home/<user>/.ssh:
	id_rsa
	id_rsa.pub


/etc/ssh/sshd_config file critical items:
Port 22
StrictModes yes

AuthorizedKeysFile /usr/NX/home/nx/.ssh/authorized_keys2

AllowUsers user1 user2 nx


RSAAuthentication yes

PubkeyAuthentication yes

PasswordAuthentication yes





These permissions are critical:
# pwd

/usr/NX/home/nx/.ssh

# ls -l

total 20

-rw-r--r-- 2 nx   root    2736 2008-10-02 19:25 authorized_keys2

-rw-r--r-- 2 nx   root    2736 2008-10-02 19:25 default.id_dsa.pub

-rw------- 1 root root    1675 2008-10-02 19:24 id_rsa

-rw-r--r-- 1 nx   nogroup  782 2008-10-02 19:20 known_hosts

-rw-r--r-- 1 root root    1061 2008-10-02 19:12 SAVEauthorized_keys2

# 



Hope this helps others who have lost NXServer.

NXServer really is great when its working but it can be a bear to fix.

Carl

---

