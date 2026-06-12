---
title: "Ubuntu set up questions"
date: 2012-08-09
forum: New to Ubuntu
---

### Post by mrsj1984 on 2012-08-09
Good Morning Guys,
 
I'm having a few dilemnas with regard to setting up through Ubuntu, I have a few questions that I can't find the answers to anywhere...
 
I'll start from the beginning..
 
I'm looking to set up my OS as Ubuntu from Windows XP, I'm on a shared network with shared emails, file access etc. The other pc's at the moment will be staying on Windows as my system is being used as a pilot.
 
I understand from what I've read that file sharing between different OS works fine, I know I can open word/excel files etc without hassle which is great. My query is with regards to the shared inboxes, is it possible to access these the same way as with Outlook?
 
I'm also struggling to set up my USB as a boot system as I can't locate the ISO file needed.
 
I was going to install Ubuntu on a seperate HD so that I could switch back to the original set up if needed however it seems that the other towers I have picked apart in the office are from the dark ages and so doing this is no longer an option, is there a way of successfully having both on one HD without causing problems?
 
Can anyone help a Ubuntu novice look fantastic in front of her colleagues??? [IMG]http://linuxforums.org.uk/Smileys/default/shocked.gif[/IMG]
 
Thanks guys
Linz

---

### Post by ranger1021994 on 2012-08-09
>>As long as Outlook is concerned you can easily setup mail client on Ubuntu via Thunderbird/Evolution (They are mail clients like Outlook)

>>You can have XP and Ubuntu on same PC.All you need to do is create a new partition and install Ubuntu on it :)

>>Using Ubuntu gives you many bragging rights.
-If you want to impress colleagues by presentation,install Compiz it add many special effects to your desktop
-Ubuntu is very damn fast,so you can open many windows and brag about speed
-Perform terminal commands (Terminal is the Command prompt of Linux) and it will stun your colleagues
That'll definitely make u look fantastic

---

### Post by epsilonpi on 2012-08-09
Why not install Ubuntu on virtualbox. That way you can use both the Operating Systems. Here is a good tutorial [http://www.psychocats.net/ubuntu/virtualbox]("http://www.psychocats.net/ubuntu/virtualbox").
:D

---

### Post by Kalanac on 2012-08-09
Virtual boxes split your system resource between the real and virtual environments.  There is really no point unless you need to have both operating systems running at once or you would be switching between them so frequently as to be annoying.

---

### Post by mkstallings1 on 2012-08-09
I agree that Thunderbird is great for your emails.  The .iso for ubuntu is available from [http://www.ubuntu.com](http://www.ubuntu.com).  You haven't told us any of the specs of the hardware you are planning on installing ubuntu.  You may not b happy with the performance if your hardware is very old.  You typically need 1 GB ram to have a snappy system. I run ubuntu on two machines, one with 750 MB and one with 2 GB and the 750 MB, for me, is bare minimum.  If your hardware has very low specs, there are alternatives such as Xubuntu, Lubuntu, or Bodhi.  These are based on ubuntu, but can run on lower resources.  Bodhi I think is the prettiest of the low resource crowd.  As far as the partitioning, ubuntu easily walks you through that during the install.  It really couldn't be easier.

---

### Post by mrsj1984 on 2012-08-09
Thank you all.
 
I've now found an 80gb hdd, now just need to locate a spare cable and reformat, I think it may be easier than to flick between partitions. I hate having to wait though that is my problem, looks like I'll be sorting it tomorrow instead...
 
I'm hoping it's going to work perfectly... fingers crossed
 
Linz

---

### Post by mrsj1984 on 2012-08-09
Thankfully I'm on 1gb so it should be ok :)

---

### Post by mastablasta on 2012-08-09
> **mrsj1984 said:**
>  
I understand from what I've read that file sharing between different OS works fine, I know I can open word/excel files etc without hassle which is great. My query is with regards to the shared inboxes, is it possible to access these the same way as with Outlook?
Yes. IMAP email access in one of the clients.
 
> 
I'm also struggling to set up my USB as a boot system as I can't locate the ISO file needed.
If oyu have 64 bit os you can use 64 bit image otherwise 32 bit should do. use unetbootin or linuxliveusb to "burn" the image on USB.
 > 
is there a way of successfully having both on one HD without causing problems?

yes. it's called dual booting (either via Wubi or propper side by side system install). GRUB boot loader is used (by default) to offer you a menu where you select the OS you want to boot.
  
 
Also for old/ancient hardware there is DSL (with old debian kernel), Slitaz, AntiX (debian testing with patched kernel to support old computers), Chrunchbang (debian, but made really easy to install and use and with low system requirements), Bodhi linux (ubuntu based, low requirements), Lubutnu (Ubutnu with LXDE, low requirements).

---

### Post by audiomick on 2012-08-09
> **mastablasta said:**
> yes. it's called dual booting (either via Wubi ...

I gather Wubi is not intended for long term use on a production system. Since you have located a second drive that you can use specifically for Ubuntu, I would suggest to not mess around with Wubi.

[http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29]("http://en.wikipedia.org/wiki/Wubi_%28Ubuntu%29")

---

### Post by mrsj1984 on 2012-08-09
Hi Michael,

Thanks for all your help.

I've installed and am now battling upgrading (it's a long story and I've posted on the Installation and Upgrade topic)

I think this may be a bit more of a task than I first thought... sigh...

---

