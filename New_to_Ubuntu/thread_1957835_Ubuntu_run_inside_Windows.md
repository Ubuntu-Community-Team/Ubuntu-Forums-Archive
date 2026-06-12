---
title: "Ubuntu run inside Windows"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by Septuagenarian on 2012-04-13
Just wondered if anyone has any experinces to share regarding running Ubuntu inside Windows XP ? In particular , what are the chances of virus migration ? There doesn't seem to be a separate partition created .

---

### Post by roelforg on 2012-04-13
You mean vm or wubi?

---

### Post by zombifier25 on 2012-04-13
Once I ran Ubuntu in VirtualBox once. Pretty smooth (if you have enough resources of course)
And about your question of viruses, I don't think Windows viruses can touch the Ubuntu partition, since the partitions are stored in a special disk image (both WM and Wubi).

---

### Post by roelforg on 2012-04-13
> **zombifier25 said:**
> Once I ran Ubuntu in VirtualBox once. Pretty smooth (if you have enough resources of course)
And about your question of viruses, I don't think Windows viruses can touch the Ubuntu partition, since the partitions are stored in a special disk image.
 
And even if thet could, neither windows nor the viruses can handle ext3/4 filesystems.

---

### Post by mastablasta on 2012-04-13
> **roelforg said:**
> And even if thet could, neither windows nor the viruses can handle ext3/4 filesystems.
 
 
but they can affect and corrupt the virtual disk file. same goes for wubit. if that disk file get's corrupted (doens't have to be virus) you loose everything in wubi. to separate the systems completelly dual boot is required. 
----
 
 
if you want to install inside windows you can use virtual box. it's very easy to setup and install. [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
 
it's a good option for safe browsing. you can then use linux to browse the net and if anything goes wrong in it you just delete the virtual OS. also no need to reboot when launching it. but you do need to have at least 2GB RAM to run the OS nicely on windows.

---

### Post by Septuagenarian on 2012-04-13
Perhaps I didn't make myself clear , on the installation CD it has the option of running Ubuntu actually within Windows XP just like any other program , so wondered if any viruses harmless to linux might infect Windows as there is no partition to keep them separate .

---

### Post by Curtis6767 on 2012-04-13
Yes, install it using WUBI.

Use it that way for as long as you like.

If it doesn't work for you, then just go to your Windows Add/Remove and you can uninstall it as if it were any other program.

If it works for you and you don't have problems with old drivers and other compatibilities, then you can look into a dual boot type install.

---

### Post by mastablasta on 2012-04-13
> **Septuagenarian said:**
> Perhaps I didn't make myself clear , on the installation CD it has the option of running Ubuntu actually within Windows XP just like any other program , so wondered if any viruses harmless to linux might infect Windows as there is no partition to keep them separate .


that is a Wubi install. 
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
Guide with plenty pictures....
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

yes if they get a windows virus they can pass it on to windows (even if it's a dual side by side boot). just like you can move virii via CD or USB you can mount the windows volume and transfer it there. however windows malware doesn't affect Linux and since they don't run on linux, linux can't automaticly pass it on (even in Wubi install) to windows maschine. it can't automaticly infect windows drive but it can infect it if you move the infected file manually (by hand, click drag and drop) to windows part and then run it on windows. you can also pass it on if it's part of an infected email.

you can use virus scan in linux if you wish. though they scan for windows malware.

Here is an nice article on the basics of security in Linux: [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

for more info on this you can read here: 
[https://help.ubuntu.com/11.04/ubuntu-help/net-security.html](https://help.ubuntu.com/11.04/ubuntu-help/net-security.html)
[https://help.ubuntu.com/community/Security](https://help.ubuntu.com/community/Security)
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Very informative thread from a forum member:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Paqman on 2012-04-13
> **Septuagenarian said:**
> Perhaps I didn't make myself clear , on the installation CD it has the option of running Ubuntu actually within Windows XP just like any other program , so wondered if any viruses harmless to linux might infect Windows as there is no partition to keep them separate .

Just to make things a little clearer: Wubi is an *installer* for Ubuntu that runs under Windows. What it does is create a virtual disk that's actually just a big file on your Windows partition, then it installs Ubuntu into that. Once you're booted into Ubuntu, only Ubuntu is running.

So it's not Ubuntu that is running as a Windows program, just the Wubi installer.

As such it is effectively a dual boot, and the two systems should be considered separate from a security point of view.

---

### Post by Septuagenarian on 2012-04-14
Many thanks to the forum members for their informative replies .

---

