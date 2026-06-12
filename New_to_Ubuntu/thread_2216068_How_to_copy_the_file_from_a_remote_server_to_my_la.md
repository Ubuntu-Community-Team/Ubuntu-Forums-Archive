---
title: "How to copy the file from a remote server to my laptop?"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by peng2 on 2014-04-09
[FONT=arial]Hi, I need to copy some files from a server in university. I've logged in the server through my laptop. And find the folder of the file I need, but I don't know how to copy.

I've tried 
[/FONT][FONT=arial]**scp <file> <username>@<IP address or hostname>:<Destination>**

but it doesn't work. My laptop is connected wifi, is that make a different?[/FONT]

---

### Post by Hadaka on 2014-04-09
hi here is a link to give you some ideas..
[http://www.hypexr.org/linux_scp_help.php](http://www.hypexr.org/linux_scp_help.php)

note that you do not do...ssh scp  bla bla bla
it is scp only.  common error when learning

also...man scp or google it.

have fun.

---

### Post by SeijiSensei on 2014-04-09
Are you running openssh-server on the destination machine?  You need that so scp can set up an SSH tunnel.  Run "sudo apt-get install openssh-server" on your machine and see if that helps.

It's also not obvious what you mean when you say you are "connected" to the remote server?  Are you logged in on that machine, or do you just have access to file shares?  If you are logged in on the remote, can you run a mail client (even maybe alpine)?  Then you could just mail the files to yourself.

If the remote server supports SSH access, then you could try copying the files to your computer by using
```
scp user@remote:/path/to/some/file /path/to/local/destination
```

---

### Post by papibe on 2014-04-09
Hi peng2.

I imagine that you're connecting to the server from home, so you have a router and you're behind NAT.

In this case, you would have to have resolved all issues to connect remotely from the Internet to your server at home in order to 'push' the files from the server.

Since you have remote ssh access to the server, I'd recommend 'pulling' the files from your computer.

Open a terminal, do not connect to the server, and run locally something like:
```
scp serveruser@remoteserver:path/to/file  ./
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by HermanAB on 2014-04-10
"I've logged in the server through my laptop."
So now you are at the server.  If you want to copy from there, you got to run a SSH server on your laptop as well, which you probably won't be able to do due to a firewall somewhere.

Log out of the server.  From your laptop local prompt, do scp with the full path of the file on the server.

---

### Post by peng2 on 2014-04-10
Many thanks to you all! Problem solved.

---

### Post by peng2 on 2014-04-10
yeah, you're right. 'pulling' files from remote server works fine. Thanks for help.

---

### Post by peng2 on 2014-04-10
> **papibe said:**
> Hi peng2.

I imagine that you're connecting to the server from home, so you have a router and you're behind NAT.

In this case, you would have to have resolved all issues to connect remotely from the Internet to your server at home in order to 'push' the files from the server.

Since you have remote ssh access to the server, I'd recommend 'pulling' the files from your computer.

Open a terminal, do not connect to the server, and run locally something like:
```
scp serveruser@remoteserver:path/to/file  ./
```
Hope it helps. Let us know how it goes.
Regards.


Hi papibe, I have another question. If I want to 'push' the file from the remote server to my local folder, how should I do it?

---

### Post by papibe on 2014-04-10
> **peng2 said:**
> Hi papibe, I have another question. If I want to 'push' the file from the remote server to my local folder, how should I do it?
There a few ways to accomplish that. First you need a service running on your home computer. The common tools most of us use is openssh, as SeijiSensei suggested. Install it like this:
```
sudo apt-get install openssh-server
```
As an easy, and ***temporary*** solution, you can use a reverse ssh tunnel:

On your home machine connect to the server:
```
ssh -R 23456:localhost:22  serveruser@remoteserver
```
enter the password and login normally.

You have created a reverse tunnel from the server on port 23456 to your home computer's port 22 (sshd). Now you can run this on the current session on the server and 'push' the file to your home machine:
```
scp -oPort=23456  /path/to/file  your_home_machine_user@localhost:
```
Once you have copied your file, you logout and the reverse tunnel is destroyed. 

For a permanent way to access your home computer from the Internet take a look at this post [here]("http://ubuntuforums.org/showthread.php?t=2172027&p=12777387#post12777387").

Hope it helps.
Regards.

---

