---
title: "how do you uninstall wubi safely?"
date: 2012-03-05
forum: New to Ubuntu
---

### Post by rima on 2012-03-05
Hiya  Just a quick question to verify  All I have to do is Add/Remove Programs in Windows XP and click on &quot;Ubuntu&quot; and that's it?   Or I heard you have to modify the boot.ini script or something?   Yes I'm that stupid XD But I don't want to lose my Windows XP or not being able to boot or something   I actually like Ubuntu very much yet I found problems with it and it was actually quite a bit slow too. Still love it though. Thanks  rima

---

### Post by seawolf167 on 2012-03-05
Just uninstall it through Add/Remove Programs in XP and you are good to go. [Here ]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")is the official documentation for uninstallation (for Windows 7 though)

---

### Post by rima on 2012-03-06
Ok i see XD But...I have a question.  I plan on trying out Wubi again (3 weeks is not enough for me to get to know around Linux perfectly...) but will the same problems happen? Like me not being able to get to Recovery mode or something? Or should I just stick with good ol' Windows?  BTW I was also planning on installing Lubuntu, since Ubuntu's really using a lot of resources so yeah. Like straight after i accidently get off my power source BOOM. it shuts down. I can't really help it, and that's the only bad thing that happened to me.

---

### Post by seawolf167 on 2012-03-06
> **rima said:**
> but will the same problems happen? Like me not being able to get to Recovery mode or something?

I don't know what problems you are referring to since you never mentioned any. Please post more details about the issues you were having.

---

### Post by rima on 2012-03-06
Oh I posted about it a while ago...I can't seem to find it now, sorry. :( But do you think that if my rubbish LG netbook managed to run Ubuntu, will it also manage to run Lubuntu? Just wondering

---

### Post by seawolf167 on 2012-03-06
LUbuntu is the light-weight version of Ubuntu, so not only will it run it, but it should run faster.

---

### Post by yetiman64 on 2012-03-06
> **rima said:**
> Oh I posted about it a while ago...I can't seem to find it now, sorry. :(...
Simple way to find your older posts, click on your user name in any of your posts, select "Find More Posts by rima", doing so here gets 46 results where you have only 44 beans (a couple of your posts must be in the cafe). Cheers.

---

### Post by Ms. Daisy on 2012-03-06
rima, I found the problems you were referring to here:

[http://ubuntuforums.org/showthread.php?t=1906141](http://ubuntuforums.org/showthread.php?t=1906141)

Lubuntu and Ubuntu are very similar, they have terminal, they're built from a Debian base, they use sudo.  So everything you learned from your Ubuntu experience will be useful for Lubuntu.

---

### Post by sudodus on 2012-03-06
I would suggest that you try to install [KXL]Ubuntu as dual boot this time, because that is more stable and also more efficient (faster) than as a program run within Windows as you were doing with Wubi.

But first you should make sure that your hard drive is suitable for that (size, configuration), so please post the results of the following terminal commands: first
```
sudo fdisk -lu
```then mount all partitions available and run
```
df
```If you have already deleted Ubuntu, you can boot from the install CD or USB drive and run a live session 'test Ubuntu' and run those commands.

Also I would suggest that you test several flavours of [KXL]Ubuntu before deciding to install.

---

### Post by Mark Phelps on 2012-03-07
Sigh ... more Wubi MIS-information ...

Wubi is NOT "a program running within Windows".  Wubi is an INSTALLER that runs within Windows.  Once you install it and then launch Ubuntu, it's running by itself.

---

### Post by sudodus on 2012-03-07
> **Mark Phelps said:**
> Sigh ... more Wubi MIS-information ...

Wubi is NOT "a program running within Windows".  Wubi is an INSTALLER that runs within Windows.  Once you install it and then launch Ubuntu, it's running by itself.
I'm reading and learning. Is it OK to ask a few more questions here or would you prefer a separate thread for that purpose?

---

### Post by rima on 2012-03-07
It's ok, I get it now XD But in Add/Remove programs, it comes up as Ubuntu....NOT wubi. so I guess I just click on it and re-install....yeah?  BTW let's say if I wanted to run Ubuntu/Lubuntu from somewhere else. i don't have a CD port,but I still want to run Live CD. What do I do?

---

### Post by sudodus on 2012-03-07
> **rima said:**
> It's ok, I get it now XD But in Add/Remove programs, it comes up as Ubuntu....NOT wubi. so I guess I just click on it and re-install....yeah?  BTW let's say if I wanted to run Ubuntu/Lubuntu from somewhere else. i don't have a CD port,but I still want to run Live CD. What do I do?
Instead of a live CD use can make a live USB drive, for example using Unetbootin. This is used very often, and many threads at the Ubuntu Forums discuss USB boot drives (how to make them and how to use them) for example [[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

Another alternative is to get an external (USB) CD drive.

---

### Post by rima on 2012-03-07
Oh thanks for the help guys :D I'll try Lubuntu...*searches for USB*

---

### Post by sudodus on 2012-03-07
> **Mark Phelps said:**
> Sigh ... more Wubi MIS-information ...

Wubi is NOT "a program running within Windows".  Wubi is an INSTALLER that runs within Windows.  Once you install it and then launch Ubuntu, it's running by itself.

***Mark***, can you tell me/us a little more about wubi?

How does it compare to
1. a regular install (single or dual boot on HDD)
2. virtual machine (e.g. VirtualBox)
3. live CD or USB
How independent is Ubuntu in Wubi? Is windows using CPU, RAM, and/or HDD file system?

Or can you refer to a good explanatory text?

---

### Post by yetiman64 on 2012-03-07
@ sudodus, Mark is right, from [[COLOR=Blue]--here--[/COLOR]]("http://wubi.sourceforge.net/faq.php") (wubi.sourceforge.net/faq, quite a bit down the page) 

>              **[SIZE=2]How does Wubi work?[/SIZE]**

             Wubi adds an entry to the Windows boot menu which allows  you to run Linux. Ubuntu is installed within a file in the Windows file  system (c:\ubuntu\disks\root.disk), this file is seen by Linux as a real  hard disk.
         
                       **[SIZE=2]Is this running Ubuntu within a virtual environment or something similar?[/SIZE]**

             No. This is a real installation, the only difference is  that Ubuntu is installed within a file as opposed to being installed  within its own partition. Thus we spare you the trouble of creating a  free partition for Ubuntu. And we spare you the trouble to have of  having to burn a CD-Rom.
         
It's a pretty in depth write up, should answer most if not all your questions.

Regards, yetiman64.

---

### Post by sudodus on 2012-03-07
> **yetiman64 said:**
> @ sudodus, Mark is right, from [[COLOR=Blue]--here--[/COLOR]]("http://wubi.sourceforge.net/faq.php") (wubi.sourceforge.net/faq, quite a bit down the page) 

It's a pretty in depth write up, should answer most if not all your questions.

Regards, yetiman64.
Thank you yetiman64 :-)

---

