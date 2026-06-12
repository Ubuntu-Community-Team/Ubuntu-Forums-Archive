---
title: "Do you need Anti Vrus Software in Ubuntu?"
date: 2008-08-23
forum: Recurring Discussions
---

### Post by mattcadu on 2008-08-23
??

---

### Post by dje on 2008-08-23
the short answer is no. windows viruses cannot affect ubuntu and there are no known viruses that affect ubuntu

dje

---

### Post by SNuxoll on 2008-08-23
As said by dje, Windows viruses cannot affect a Linux machine.  However, if you are emailing friends with Windows boxes it is generally a nice thing to install ClamAV and scan files you send and recieve to protect them.

---

### Post by RequinB4 on 2008-08-23
Like others said, no.

I would like to add (and this doesn't apply to you) that if you ever setup a file transfer/hosting or mail server it is good to have AV so you don't infect everyone.

---

### Post by halitech on 2008-08-23
read this thread for a clearer understanding of *nix and viruses

[http://ubuntuforums.org/showthread.php?t=897878](http://ubuntuforums.org/showthread.php?t=897878)

---

### Post by EnGorDiaz on 2008-08-23
> **dje said:**
> the short answer is no. windows viruses cannot affect ubuntu and there are no known viruses that affect ubuntu

dje

ahhh but the almighty windows has also taught us all about the pie in linux and unix terms ubuntu takes the pie i would look at this thread

[http://free.avg.com/ww.download?prd=afl](http://free.avg.com/ww.download?prd=afl)
here you go avg 

now you should always look at .sh scripts in gedit before launching them dont use commands like these

sudo startx

and watch out for most -rm commands in there could be a destruction script and you dont know because ubuntu is voted one of the most user friendly and secure of linux doesnt mean crap you dont activate some commands check your scripts 

tarball bombs there another thing you have to look out for..


one more thing most of these viruses and exploits are under redhat and have been patched but hers a list

[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)

---

### Post by kansasnoob on 2008-08-23
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by damis648 on 2008-08-23
Repeat: No. Just be careful running commands as root.

---

### Post by jamesrfla on 2008-08-23
You only need anti-virus if you are sharing files with windows and you want to scan those files before you put then on another windows computer. If not the answer is no. You also don't need a firewall unless hosting a web server.

---

### Post by jwkungfu on 2008-08-23
I converted to Ubuntu quite a few months ago and use the internet daily.

I have NO anti virus.

I have NO virus' or problems.

Welcome to Linux-land!

:guitar:

---

### Post by niccholaspage on 2008-08-23
You don't need an Anti Virus Program unless you send files between Windows Users because if you transfer that file to another Windows PC... Eh.I would say you don't need any.

---

### Post by aysiu on 2008-08-23
Even if an actual virus threat for Linux appeared in the wild, having antivirus software installed would not prevent your computer any more than other Ubuntu computers (ones without antivirus) from being infected. Think about it.

---

### Post by Twitch6000 on 2008-08-24
How many times am I going to blow my head off about these topics =[.

Read this that was a great reply on the same kind of topic.
Which again i am begging the mods to make as a sticky.

> **lukjad007 said:**
> First of all, read this:
[http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

These are the two main questions you seem to have:

Are there and Anti-Viruses for Linux?
Are there any viruses for Linux?

For the first one, Yes.

For the second one, yes... and no.

As my esteemed colleague, Twitch6000, said, there are SOME viruses to be found. ***However***, they are hard to get. The difference between Linux Viruses and Windows Viruses is that Windows is always running as the root user. So, anything that happens to part of the computer, happens to all of the computer. Also, with Ubuntu most of the programs you  will ever install come from authentic repositories that are checked, double checked, and triple checked to be uninfected. If you choose in install programs from repositories other than those supported by Ubuntu, you do so at your own risk. You need to check the references of the repository you are using. If some guy you see at a cracker site tells you to activate the 1337h4xr repository, be suspicious.

The same is true about installing programs. If you install GIMP 2.50 from the GIMP's Official Website ([www.gimp.org](www.gimp.org)), you are giving them a measure of trust since they are a proven entity. However, if you go to [www.SuperCoolThingy.com](www.SuperCoolThingy.com) (I invented the site name) and start installing a bunch of programs, you may have a problem. The point of using Linux is not to be blissfully ignorant, but to be informed and cautious but not constantly in danger. Unlike in Windows, you cannot just accidentally click on a link and get infected. 

Now, if you are worried about loosing data, you need to be wary of any commands given to you. This ***_[COLOR="Red"]DANGEROUS COMMAND[/COLOR]_*** below will destroy your computer if run as root:
```
rm -rf /
```
The point is that you have to be careful, but you have a better foundation upon which to defend yourself. If ever you are suspicious of a program, don't install it until you check it out. If someone you don't trust tells you a command that you don't understand, ask someone what it does. Google is your friend. Look up what chmod is. Look up what rm -rf / does. If you don't like what you see, wait. Read [http://ubuntuforums.org/announcement.php?f=73](http://ubuntuforums.org/announcement.php?f=73) for more on dangerous commands. 

Basically, it is possible to get a virus, if you are not careful. It is also easy to destroy the usability of your computer if you do a dangerous command. 

Below is a Youtube Video I found about what happens when you run rm -rf / as root. The point is that since Windows is always root, any program can destroy the system. In Linux, especially Ubuntu, the damage is limited.

[http://www.youtube.com/watch?v=wWOjmvWPRvQ](http://www.youtube.com/watch?v=wWOjmvWPRvQ)

So basically are there viruses for Linux: YES
IS there anti virus program for Linux: YES
Do you need to be worried about getting infected with a virus: NO,Unless you toy around with wine alot then you could have some problems.

---

### Post by cardinals_fan on 2008-08-24
> **aysiu said:**
> Even if an actual virus threat for Linux appeared in the wild, having antivirus software installed would not prevent your computer any more than other Ubuntu computers (ones without antivirus) from being infected. Think about it.
Once again, the point is made.  And, once again, it is correct.

---

