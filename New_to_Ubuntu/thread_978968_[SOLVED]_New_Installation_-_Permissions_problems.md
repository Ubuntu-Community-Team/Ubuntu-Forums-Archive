---
title: "[SOLVED] New Installation - Permissions problems"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by CarolinaGuy on 2008-11-11
Newbie needs HELP

I&#8217;m new to Linux. I am attempting to set up a Home file server based on the article entitled "Simple Home File Server (Based on Ubuntu)" found at --- [http://www.howtoforge.com/ubuntu-home-fileserver](http://www.howtoforge.com/ubuntu-home-fileserver).


I have ubuntu 7.10 server edition installed.

It boots find, I enter my name for the user account (charlie) and my password. Everything's find. Next I enter the command  &#8220;su&#8221; and go to root, it requests my password and I enter the password for root.

Now I am at:
root@ubuntu: /home/charlie#

I enter */etc/network/interfaces* to edit the network and configure a static IP address.

It returns:

bash: /etc/network/interfaces. Permission denied.

I don&#8217;t understand when I&#8217;m the only user on the computer and I&#8217;m at root why I getting permission denied. And since I&#8217;m completely new to UBUNTU and don&#8217;t have a clue;  can someone suggests a remedy for this problem.

THANKS in advance for time and helping me with this problem

 CarolinaGuy**[B][B]**[/B][/B]

---

### Post by taurus on 2008-11-11
If you want to change to that directory, you need to put cd in front of the path.

```
**cd** /etc/network/interfaces
```
Without the cd, the system thinks that you want to execute /etc/network/interfaces which you can't since it's a directory.  That's why you get that error message.

---

### Post by SunnyRabbiera on 2008-11-11
you may also need the sudo command, sudo is what takes you under full administration mode.
By default Ubuntu doesnt use root, so any commands you may get for that will not be applicable.
If a guide says use su substitute it with sudo.

---

### Post by bodhi.zazen on 2008-11-11
First you should probably use sudo rather then root.

Second, you need to use an editor.

Try 

```
sudo nano /etc/network/interfaces
```

[uhelp]community/RootSudo[/uhelp]

I understand security is a double edged sword, it is frustrating sometimes. I think the average time to crack a default Windows XP install once it hits the internet is less then 5 minutes, so I guess it is probably worth the effort to learn to enhance your security :)

See if this link helps : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by bodhi.zazen on 2008-11-11
> bodhi@hardy: cd /etc/network/interfaces
cd: not a directory: /etc/network/interfaces

:rolleyes:

---

### Post by CarolinaGuy on 2008-11-11
My THANKS to a great & helpful community. I continuing with the installation of data, updates and setting up the SAMBA server.

Again MY THANKS to all who responded.

CarolinaGuy

---

