---
title: "Basic  networking services ..!!!!"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Ashudagr8 on 2008-07-08
Hi community ,

I am completely new to ubuntu. i have installed ubuntu on VM server running on windows xp.. but i am struggling to start basic services like ftp,ssh and SMB... init.d directory does not have any of the services listed... let me know how can i start basic services like FTP,telnet,smb,ssh so i can transfer data between windows and ubuntu..!!!

Thanks in advance..!!!

---

### Post by mcduck on 2008-07-08
Have you actually installed any of those services yet?

---

### Post by DezSP on 2008-07-08
These services are probably not installed yet. You can use Synaptic or apt-get to install them, for example:

sudo apt-get install openssh-server

To install SSH (and SFTP).

---

### Post by cmnorton on 2008-07-08
You need to check to see what's installed. Synaptic is good for installing but also for searching the already installed packages. You've probably installed Ubuntu desktop; some of the services you seek are not installed by default. I suggest you search for vsftp in Synaptic, and then install that.

From there, you may have to tweak settings in /etc/vsftp.conf.. 

Telnet is available but discouraged, because not everyone sits behind a firewall. I have telnetd (named that exactly) installed for my telnet daemon.

sshd is usually installed and may need to be set up to start. 

I cannot remember if samba is already installed and needs to be set to start. 

To reiterate, Synaptic is one way, not the only way, to search for what is already installed and to install new stuff. 

You will probably find that also installing build-essential is a useful thing. build-essential gives you useful program development tools.

If you have a need to convert to and from dos and unix format, tofrodos is another useful package.

---

