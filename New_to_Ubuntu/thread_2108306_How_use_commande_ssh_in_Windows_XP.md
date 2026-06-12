---
title: "How use commande ssh in Windows XP?"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by Patrix78 on 2013-01-24
Hello

i want to test ssh connection towards my ubuntu server

i want test with " ssh -vvv "



Why my ubuntu rejects my ssh connections with putty

I use Putty on WindowsXP:

i enter the ip of ubuntu server on the field "hostname"

as soon as i click on the button "Open"

Putty reject with the error :  Network error. Connection Refused


Before the installation of LAMP, it worked

In one forum, it tells me make and ssh -vvv to see what the problem

But why make this command in windows xp?

Patrice

---

### Post by The Cog on 2013-01-24
Connection Refused usually means that the Ubuntu server is not listening for incoming connections. Please try this command on your Ubuntu server, to see if port 22 is listening at all, and post the results here:
```
netstat -lnt
```
If ssh is listening for connections, you should see a line like the one below.:
```
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN   
```


As a further test, if you try to use telnet to port 22 of the Ubuntu server, you should see it announce the version of ssh it is running. Try this command on your windows PC (with the ip address of the Ubuntu server)
```
telnet 1.2.3.4 22
```
You should see an answer like this if the SSH server is running:
```
SSH-2.0-OpenSSH_6.0p1 Debian-3ubuntu1
```

---

### Post by jonobr on 2013-01-24
A few other things to try

If you open a terminal window

paste the following

```
which sshd

```
you should get something like

> /usr/sbin/sshd

If you get a not found then there is nothing listening-

also typing

```
sudo apt-get install openssh-server

```

If the response looks like this

> Reading package lists... Done
Building dependency tree
Reading state information... Done
openssh-server is already the newest version.


Then let us know as the server is installed,.

If you get a question asking for a yes/no answer,
then its most likely not installed

Select yes and try to connect once its completed

---

### Post by sudodus on 2013-01-24
You can also check that the SSH service is really running by
```
ps -A|grep sshd
```
It should return a line with the pid (some 4 digit number) like
```
 1026 ?        00:00:00 sshd
```
If you need the real ssh client tools at the other computer, you can boot that computer from an Ubuntu boot CD or USB drive and try either of

```
ssh user@server-ip
``` or
```
sftp user@server-ip
``` where [FONT="Courier New"][SIZE="3"]user@server-ip[/SIZE][/FONT] might be something like [FONT="Courier New"][SIZE="3"]patrix@192.168.0.2[/SIZE][/FONT]
I am assuming that you do this in a local area network.

If sshd is running and you cannot connect, maybe the ssh port was closed at the installation of LAMP.

---

### Post by Patrix78 on 2013-01-25
Hello,
thanks for your advices

Unfortunately, i have not acces to the server physically (it's a remote dedicated server) and I cannot connect to the server ( ssh connection not works)

The server is an Ubuntu Desktop 12.04

********************************
BEFORE the problem happens

I have just install LAMP (with tasksel) 

and i do this :   su root
sudo passwd root

now, all putty connections ssh failed

********************************

I read your advices

i do netstat, there are not tcp connection on port 22

i do a 
telnet ip_ubuntu 22
Connect to ip_ubtuntu....Impossible to open a connection to the host, on the port 22 : Connection failure


**********************************

a good news is that i have a rescue mode that permit start server on a linux/BSD and i can explore all the files on the ubuntu desktop

The problem is i'm a absolute beginner in linux

i have edited hosts.allow and i have written ALL:ALL and the problem is not solved

***********************************

I think the only thing to do is search a usb key to install Ubuntu Boot CD

Patrice

---

### Post by sudodus on 2013-01-25
I suggest that you ask the person who is in charge of the server how to connect to it, for example which port to use and ask for the method (for example to get a public key or a password).

Then it should be possible to connect using ssh from a live system or using putty from Windows as before.

---

### Post by Patrix78 on 2013-01-25
I have forgotten to say that only ssh connection failed

ping works

ftp server works

http webserver works

Thanks for any help

I can reinstall the server because i have just install LAMP

but i would like understand

i want to learn

Patrice

---

### Post by Patrix78 on 2013-01-25
The public key or the password is stored in which files?

I can access all the files in the server

Patriec

---

### Post by sudodus on 2013-01-25
Do I understand correctly: you are the administrator of the server, and it is remote (as seen from the windows computer)?

Is it far away, or can you go to it fairly easily? If you can go there easily, can you try to connect locally, when you are there?

Could there be a problem with a firewall between the server and the windows computer? Could it be that a firewall in the server computer was activated by the installation of LAMP? (I have not used LAMP, so I don't know what it does to the system.)

Maybe you can find something useful in this link

[[COLOR="Red"]https://help.ubuntu.com/10.04/serverguide/openssh-server.html[/COLOR]]("https://help.ubuntu.com/10.04/serverguide/openssh-server.html")

---

### Post by sudodus on 2013-01-25
> **Patrix78 said:**
> The public key or the password is stored in which files?

I can access all the files in the server

Patriec

public key: see the link in post #9

password: to use a password you need a user account on the server. Use the password of that user account! But in systems with high security, password is disabled for ssh.

---

### Post by Patrix78 on 2013-01-25
Yes, I am the administrator of the server.

I use the remote program X2Go Client on Windows XP to access on the server

The remote program use ssh connection, so, the remote connection do not work

It's not a problem of firewall, because  in rescue mode, I can access on the Linux/BSD via the ssh connection.

Moreover, if i reinstall the ubuntu, it will works. I have already done.
But i do not want to reinstall, i want to understand why it do not work

thanks for the idea:

the parameter for ssh connection is in sshd_config
i can try to save it, and replace it from the sshd of the Linux/BSD

Patrice

---

### Post by Patrix78 on 2013-01-25
Yes, I am the administrator of the server.

I use the remote program X2Go Client on Windows XP to access on the server

The remote program use ssh connection, so, the remote connection do not work

It's not a problem of firewall, because  in rescue mode, I can access on the Linux/BSD via the ssh connection.

Moreover, if i reinstall the ubuntu, it will works. I have already done.
But i do not want to reinstall, i want to understand why it do not work

thanks for the idea:

the parameter for ssh connection is in sshd_config
i can try to save it, and replace it from the sshd_config of the Linux/BSD

Patrice

---

### Post by Patrix78 on 2013-01-25
Yeah

I create un bootable key with Ubuntu !

I open the terminal and i put :

ssh -v ip_ubuntu

OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1:Connecting to ip_ubuntu [ip_ubuntu] port22.
debug1:connect to address ip_ubuntu port 22: Connection refused
ssh: connect to host ip_ubuntu port 22 : Connection refused

Are they errors in line 19 of sshd_config?

Hummm

---

### Post by SlugSlug on 2013-01-25
I've had tasksel remove programs on me in the past. If you used this to install LAMP it may MAY have uninstalled ssh

---

### Post by Patrix78 on 2013-01-25
yes, you're right, some users says do not use LAMP, because it uninstall package!!!

Another user in another forum, said he had to reinstall openssh to resolve this problem

But, how connect to ubuntu without ssh connection ???

how use telnet to connect ?

Patrice

---

### Post by sudodus on 2013-01-25
In the server:

- Is sshd running?

- Is the ssh port (no 22) open?

- Is sshd listening to that port or to another port?

---

### Post by SlugSlug on 2013-01-25
> **Patrix78 said:**
> yes, you're right, some users says do not use LAMP, because it uninstall package!!!

Another user in another forum, said he had to reinstall openssh to resolve this problem

But, how connect to ubuntu without ssh connection ???

how use telnet to connect ?

Patrice


You need physical access now

---

### Post by sudodus on 2013-01-25
> **SlugSlug said:**
> You need physical access now
+1

I agree with SlugSlug

---

### Post by jonobr on 2013-01-25
This thread is going in circles.

Respectfully, if you the administrator, then administer.
Something is broken and I do feel your pain, but you need to either delegate someone to be your eyes on the ground and walk them through it , changing the password when you finish, or go there yourself.

---

