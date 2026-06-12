---
title: "Ubuntu won't log in"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by lukelongbeard on 2008-07-13
Hey, I've posted several threads detailing my attempts to get Ubuntu or some other linux client working here and on the linux.org forums.  

I tried Mepis as suggested by someone here, and it worked better than most so far, but it wouldn't recognize the wireless LAN card I have installed and I was told that I should probably get the latest version of Mepis (I got 5.0 from the internet for some reason).  Rather than go redownload a newer Mepis, since the problem I was having appeared to be with a missing driver in the kernel, I went ahead and installed Ubuntu on the partition I previously created for Mepis.

Now that I have Ubuntu installed I am having the same ole problem I've been having since early June.  Why can no one help me with this?

Ubuntu WILL NOT let me log in.  I enter my username and password, it tries to load and kicks back out to the login screen. 

Can I get some real help here PLEASE?!?!? I've been at this since May, started trying Ubuntu in June.  If Ubuntu is so much better than Windows, why can't I even login?  Help has been so scarce I'm about to give up on Linux.

---

### Post by phidia on 2008-07-13
If when you enter your password you end up back at the login screen either you are not using the correct password (check your caps lock key) or there is something wrong with the install.
Press Alt+Ctrl+F2 you should get a commandline with a cursor. Can you login there?

---

### Post by lukelongbeard on 2008-07-13
I KNOW there is nothing wrong with the password.  This is not something as simple as that.  I will try the command line prompt and post my results.

---

### Post by lukelongbeard on 2008-07-13
Okay, tried ctrl alt f2, and the screen froze up.  My prior experience trying to solve this problem suggested that it has something to do with the video drivers or the monitor.  The screen freezing seems to support that yet again.  Anyone?

---

### Post by SunnyRabbiera on 2008-07-13
hmm, well installing one linux on top of another linux can do this, especially if you are using the same home partition.

---

### Post by phidia on 2008-07-13
> **lukelongbeard said:**
> Okay, tried ctrl alt f2, and the screen froze up.  My prior experience trying to solve this problem suggested that it has something to do with the video drivers or the monitor.  The screen freezing seems to support that yet again.  Anyone?

You can try using a livecd (knoppix, ubuntu & others) to look at the install. If you think it's the video driver you can change that in /etc/X11/xorg.conf 

Look for the device section and where the driver is listed replace it with "vesa" See if that let's you log in.

---

### Post by lukelongbeard on 2008-07-13
> **SunnyRabbiera said:**
> hmm, well installing one linux on top of another linux can do this, especially if you are using the same home partition.

partition was reformatted during install.  had this problem before there was any other linux os on the partition as well.  had this same problem from ubuntu liveCD, as a matter of fact.

---

### Post by lukelongbeard on 2008-07-13
> **phidia said:**
> You can try using a livecd (knoppix, ubuntu & others) to look at the install. If you think it's the video driver you can change that in /etc/X11/xorg.conf 

Look for the device section and where the driver is listed replace it with "vesa" See if that let's you log in.

Someone at freegeek suggested knoppix, perhaps I will try it.  I'm just getting tired of downloading one thousand different liveCDs and OSes, none of which have worked well or at all, as of yet.  

Using Ubuntu liveCD I have this same problem.  It can't even start up Ubuntu with a liveCD.

How do i access /etc/x11/xorg.conf?  from the ubuntu recovery mode, i selected root shell prompt.  typed just the directory and typed cd +directory.  Both times got this message: No such file or directory.

Thanks all for your continued help.

---

### Post by lukelongbeard on 2008-07-13
Maybe I should mention that there is an apparent long standing history of ATI video cards having driver problems with linux operating systems and that the on board video on my motherboard is, indeed, an ATI graphics card.  

The problems are such that there is a wiki specifically addressing the issues here [http://wiki.cchtml.com/index.php/Main_Page]("http://wiki.cchtml.com/index.php/Main_Page")

I am not sure which version of Ubuntu I am running, but trying the command prompts it suggests to install the drivers the Ubuntu way do not work.

I could really use some help either switching the driver to vesa or selecting the proper ATI drivers.

---

### Post by esbo on 2008-07-13
I had what sounds like a very similar problem but it is hard to say as your description was too vague.
There was a solution however I used a different version which worked anyway.

---

