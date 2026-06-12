---
title: "Hi I dont know how to work ubuntu"
date: 2012-02-03
forum: New to Ubuntu
---

### Post by Satoyaki on 2012-02-03
okay i just installed linux ubuntu, and to be honest everything seems pretty obvious, but what if your computer with linux on it doesnt have the internet, then how do you install programs. i have access to another computer (running windows) that has the internet and a usb drive, but i cant seem to download a program on that computer and transfer it to my laptop (running ubuntu). how do install programs on Ubuntu without an internet connection?

---

### Post by cortman on 2012-02-03
I may have just the thing for you- see the link in my signature on offline software installation- download with Windows.

---

### Post by Satoyaki on 2012-02-03
hope this works. fingers crossed

EDIT: I dont understand the synaptic thing. is there an easier way. something i can just point and click?

---

### Post by sikander3786 on 2012-02-03
Welcome to the forums. :)

And further reading here:

[http://www.tuxgarage.com/2011/07/offline-package-installation-synaptic.html](http://www.tuxgarage.com/2011/07/offline-package-installation-synaptic.html)

And you would probably want to keep your offline PC updated also however it is a bit complicated:

[http://www.tuxgarage.com/2011/07/offline-upgrade-install-packages-ubuntu.html](http://www.tuxgarage.com/2011/07/offline-upgrade-install-packages-ubuntu.html)

---

### Post by Satoyaki on 2012-02-03
> **sikander3786 said:**
> Welcome to the forums. :)



thanks


EDIT:

> **sikander3786 said:**
> 

[http://www.tuxgarage.com/2011/07/offline-package-installation-synaptic.html](http://www.tuxgarage.com/2011/07/offline-package-installation-synaptic.html)



thats refering me to a download script. how am i supposed to use that if my linux compter has no internet?



EDIT:

Ive been trying for hours. there seems to be no way to download the files on a windows computer and then install them on an ubuntu computer.

or at least not a way that i can grasp, being new to linux


EDIT:
How is ubuntu superior to windows if you have to do all this work just to install a program.

---

### Post by sikander3786 on 2012-02-03
Missed to mention that if you are using Ubuntu Oneiric, chances are that Synaptic isn't installed as it doesn't come with Synaptic by default. You'd first need to install Synaptic. Yeah, its a pain but thats how everything works around here. :)

Just checked and hope it won't be hurting as much as I thought as it was pulling only one missing dependency on my PC. So, you need to download these packages for your architecture (amd64 = 64-bit, i386 = 32-bit) and install them one by one by double clicking at them:

[http://packages.ubuntu.com/oneiric/libept1](http://packages.ubuntu.com/oneiric/libept1)
[http://packages.ubuntu.com/oneiric/synaptic](http://packages.ubuntu.com/oneiric/synaptic)

Then proceed with any of the tutorials linked already.

---

### Post by Satoyaki on 2012-02-03
i dont get this at all its like im reading chinese... no, harder

---

### Post by Satoyaki on 2012-02-03
> **sikander3786 said:**
> Missed to mention that if you are using Ubuntu Oneiric, chances are that Synaptic isn't installed as it doesn't come with Synaptic by default. You'd first need to install Synaptic. Yeah, its a pain but thats how everything works around here. :)

Just checked and hope it won't be hurting as much as I thought as it was pulling only one missing dependency on my PC. So, you need to download these packages for your architecture (amd64 = 64-bit, i386 = 32-bit) and install them one by one by double clicking at them:

[http://packages.ubuntu.com/oneiric/libept1](http://packages.ubuntu.com/oneiric/libept1)
[http://packages.ubuntu.com/oneiric/synaptic](http://packages.ubuntu.com/oneiric/synaptic)

Then proceed with any of the tutorials linked already.

install on the windows pc with internet or the linux without internet?


BTW im using 11,10

---

### Post by sikander3786 on 2012-02-03
> **Satoyaki said:**
> install on the windows pc with internet or the linux without internet?


BTW im using 11,10
Download the packages from those links anywhere you've got an online PC whether it be Windows or Linux. Then install those packages on your target Ubuntu PC (offline one). Install the 'libept1' package first and then the 'synaptic' one.

Yeah, 11.10 is Oneiric and it doesn't come with Synaptic, sadly.

---

### Post by Satoyaki on 2012-02-03
Could you explain  what each of the terms mean, assuming i dont even know what linux is, because i have no idea how to use it or much of what you're talking about. i know how to use windows but this is very different to the point that its upsetting. i cant understand this at all and trying to figure it out is hurting my head and giving me a stomach ache.

---

### Post by Satoyaki on 2012-02-03
> **sikander3786 said:**
> Download the packages from those links anywhere you've got an online PC whether it be Windows or Linux. Then install those packages on your target Ubuntu PC (offline one). Install the 'libept1' package first and then the 'synaptic' one.

Yeah, 11.10 is Oneiric and it doesn't come with Synaptic, sadly.
k. is that all i have to do?

---

### Post by sikander3786 on 2012-02-03
> **Satoyaki said:**
> thanks


EDIT:



thats refering me to a download script. how am i supposed to use that if my linux compter has no internet?

It isn't referring you to download the script but is asking you to generate the script via Synaptic. All you need to do is to get Synaptic running on that target PC.

> EDIT:

Ive been trying for hours. there seems to be no way to download the files on a windows computer and then install them on an ubuntu computer.

or at least not a way that i can grasp, being new to linux

Be patient and you'll grab it, hopefully. ;)

> EDIT:
How is ubuntu superior to windows if you have to do all this work just to install a program.

There can be many arguments on this. We aren't taking about what is superior and what isn't. Everyone has got the freedom to choose the OS which best suits his personal needs. I mean, Windows might be the dream OS for some of us while for the others, it might be Linux or Mac blah-blah. The only thing I would suggest is that if you've come to try Ubuntu, give it some time, try to learn it and then decide which of those better suits yourself.

And you don't need to give Ubuntu 24 hours a day and 7 days a week, just keep using it whenever you need it.

---

### Post by Satoyaki on 2012-02-03
OKAY this is my fault, i should have mentioned, im running a 32 bit ubuntu 11.10. should i be running 64 if my computer can handle it or aare there benefiets to both. this is so frustrating :-(

---

### Post by sikander3786 on 2012-02-03
> **Satoyaki said:**
> OKAY this is my fault, i should have mentioned, im running a 32 bit ubuntu 11.10. should i be running 64 if my computer can handle it or aare there benefiets to both. this is so frustrating :-(
Nopes, running 32-bit is just as fine as running 64-bit Ubuntu. It isn't the right time for you to jump into the 32-bit/64-bit debate. As a one-liner, 64-bit is intended for 64-bit PCs only while 32-bit can run on both 32-bit and 64-bit PCs, almost equally well.

---

### Post by ajgreeny on 2012-02-03
It is a shame to have to say this, but as a beginner without an internet connection, you are probably going to continue to be very frustrated by linux and Ubuntu.

The whole setup of the OS is really dependent on connection to the repositories, sort of warehouses, of all the software packages that are available for the system.  It is possible to download the packages you want/need from the repositories with any computer, whichever OS it is running, but it is going to be a slow, tedious and eventually very frustrating procedure for you, and you have to know exactly what is needed, hence the use of synaptic to make a list of the packages plus dependencies needed to do that.  I have been using Ubuntu now for nearly 7 years, since version 5.04, and I would have given up long ago if I had no internet connection.

Is there any way that you can get a connection sorted for this machine, either wired or wireless?  If you can I think you will suddenly find that the operation of installing applications becomes even simpler than it is for windows.

I do not wish to completely put you off trying to use this wonderful OS, but let's make sure that a connection really is not possible first.  You can then decide whether or not it is worth the work required.

Good luck, whatever you decide.

---

### Post by QIII on 2012-02-03
ajgreeny's post raises this question:  are you without internet connection due to hardware (you don't have an ethernet cable connected) or because something is going wrong when you do have a cable connected?

---

### Post by cortman on 2012-02-03
Ajgreeny puts it a little strong perhaps- you CAN install software on offline Ubuntu machines quite easily, if you follow instructions and are willing to learn some new things.
It definitely is harder. Like he said, if you're online it becomes almost easier than Windows.

If you want, I can step you through installing Synaptic on your Ubuntu and take you through the offline installation/package download process, but you're going to have to be patient and willing to learn. Otherwise, you're probably better off with Windows.

---

### Post by krishnan t s k on 2012-02-03
If u really want to try ubuntu, u can install it inside windows through wubi installer for windows..... that way, u can have net connection for both windows and ubuntu.... another advantage is u can access your windows files in ubuntu directly.... instead of going through the pain of installing software offline, you can install it online
Ubuntu by default works with almost all hardware out of the box and it is also very easy to find and install software in 2-3 clicks through the synaptic packet manager or the ubuntu software center
You should know that wubi by default downloads and installs the 64-bit version of ubuntu.... this is no big deal.... i myself run 64-bit ubuntu on my 32-bit comp and have experienced very little hardware problems 
the link for wubi is given below
[http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer)
have a nice day and in case of any hiccups, search the forums or just post it :):)

---

### Post by LinuXofArabiA on 2012-02-03
You sure you're not just a Microsoft employee?! JK, welcome to Ubuntu, and things will get easier with time ... If you are willing to invest some time in reading and experimenting. 

Few notes:
1- Linux is virtually infinitely customizable, windows is not.
2- Linux is waaay more efficient in using your system resources. 
3- Linux online experience (web browsing) is safer and more peaceful, as opposed to Windows where you have to enter the web with shields and armor to protect yourself from all kinds of malware, spyware and what have you.

---

### Post by ajgreeny on 2012-02-03
> **cortman said:**
> Ajgreeny puts it a little strong perhaps- you CAN install software on offline Ubuntu machines quite easily, if you follow instructions and are willing to learn some new things.
It definitely is harder. Like he said, if you're online it becomes almost easier than Windows.

If you want, I can step you through installing Synaptic on your Ubuntu and take you through the offline installation/package download process, but you're going to have to be patient and willing to learn. Otherwise, you're probably better off with Windows.
OK, perhaps it was a bit strong, but let's face it, the OP was having great difficulty understanding the instructions given in earlier posts and therefore I still suspect that he/she will find the whole thing very hard to manage.

I still think it makes much more sense to first find out if the hardware being used is the cause of the connection problem, or if it is going to be impossible to make any sort of connection.  Once that is sorted, we can all try to help out with solutions for getting the wanted packages installed.

---

### Post by cortman on 2012-02-03
> **ajgreeny said:**
> OK, perhaps it was a bit strong, but let's face it, the OP was having great difficulty understanding the instructions given in earlier posts and therefore I still suspect that he/she will find the whole thing very hard to manage.

I still think it makes much more sense to first find out if the hardware being used is the cause of the connection problem, or if it is going to be impossible to make any sort of connection.  Once that is sorted, we can all try to help out with solutions for getting the wanted packages installed.

*Nods. Sounds like a plan.

---

### Post by Satoyaki on 2012-02-03
k well that was informative and sympathetic. thanks. to satisfy your curiosity... my 2010 $815can Toshiba satellite laptop I bought at "the scorce" running ubuntu is fine. the only hardware problem is   intel video card. the pentium 4 compaq desktop running windows xp with wiered internet is not mine. It belongs to the rest home i live at (which is kind of like a group home). I already asked the boss here and she said i cant hoock the ethernet cord up to my laptop. also. i ran ubuntu on the compaq from a usb stick and in ubuntu the internet wouldn't work. dont know why, maybe it has to do with the ISP. im currently trying to download DEBs onto my usb drive - OoOoOoOHh ubuntu 64 bit just finished downloading :-)
- to see if i can install them. tomorrow Im going to go try and use the library wifi, and if i cant get that ill try the starbucks. hopefully i still have some money on my starbucks gift card, as i spent the rest of my money today on a hookah and some flavoured tobacco after returning a 45 dollar digital camera that only rercords vedios with now sound :)

---

### Post by ebeth on 2012-02-03
I'm having a similar issue - I've installed ubuntu 11.10 on a Dell A90n netbook. (It was originally running an old version of Unbuntu.) Everything is fine except the wireless. On the wireless menu I have "device not ready (firmware missing)". I suspect I have the same problem. Am I correct?

Two other questions:

1. I downloaded and installed Synaptic on my laptop, also running 11.10, via the Unbuntu Software Center. How do I get this software onto the netbook?  I'll just use a USB, but what files do I need to look for?

2. Once I get Synaptic on the netbook, how can I get the package files?  (It still will not have a network connection.)  Are they on the original CD I made when I installed?

I installed Unbuntu on the netbook for a friend, but liked it so much I installed it on my laptop. I've always wanted to try Linux and this gave me a reason. I've only been using it for a day but I'm really liking it.

@cortman - didn't see the links to your tutorials.  Will try these first.

---

### Post by cortman on 2012-02-03
> **ebeth said:**
> I'm having a similar issue - I've installed ubuntu 11.10 on a Dell A90n netbook. (It was originally running an old version of Unbuntu.) Everything is fine except the wireless. On the wireless menu I have "device not ready (firmware missing)". I suspect I have the same problem. Am I correct?

Two other questions:

1. I downloaded and installed Synaptic on my laptop, also running 11.10, via the Unbuntu Software Center. How do I get this software onto the netbook?  I'll just use a USB, but what files do I need to look for?

2. Once I get Synaptic on the netbook, how can I get the package files?  (It still will not have a network connection.)  Are they on the original CD I made when I installed?

I installed Unbuntu on the netbook for a friend, but liked it so much I installed it on my laptop. I've always wanted to try Linux and this gave me a reason. I've only been using it for a day but I'm really liking it.

@cortman - didn't see the links to your tutorials.  Will try these first.

Hi ebeth. Try the procedures outlined in the tutorials, and if you have any questions post on those threads. And if you have further issues, I recommend starting a new thread. Good luck!

---

### Post by ebeth on 2012-02-04
@Satoyaki - I followed the instructions at [http://ubuntuforums.org/showthread.php?t=1901446](http://ubuntuforums.org/showthread.php?t=1901446) and was able to get the package manager running.  Now I will be able to solve my own networking issues.  

Keep at it and follow the directions carefully and you should be up and running soon.

---

