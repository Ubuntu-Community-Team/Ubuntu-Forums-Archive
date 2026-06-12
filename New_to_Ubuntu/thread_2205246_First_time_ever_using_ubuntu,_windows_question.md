---
title: "First time ever using ubuntu, windows question"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by seejay2 on 2014-02-12
This is the first time I have ever posted on any forum, so please be understanding if I am inadvertently violating the etiquette.  Also, I am a lifelong Windows user and am switching to Ubuntu, so please forgive my complete ignorance to it.  Here is my issue, any help is appreciated…
 
I have an HP Pavilion dv7 laptop that runs Windows 7 – 64 bit.  It has two hard drives, C: and D:.  Currently, C: is running Windows and D: is used for storage.  I can boot Windows, but once it loads it is almost totally unfunctional (windows explorer keeps crashing).  From what I can tell, the C: hard drive is damaged.  I would like to install Ubuntu, but I would also like to keep Windows.  I believe that is called a dual-boot.  There is plenty of information on how to do a dual boot, but with C: not working is it possible to somehow run Windows on the D: drive?  When I removed the C: drive and turned it on, it said it could not boot Windows, but recognized the D: drive.  While the obvious answer may be to put Windows on D:, I don’t know how.  The computer came with no discs and I do not have a recovery disc.  Is it possible to use C: to get Windows running on D: and then do a dual-boot with Ubuntu? 
 
Thank you.

---

### Post by Votlon on 2014-02-12
First welcome to Linux!!  >: D
secondly give me specs on how much data the 2 hard drives ( C: and D: )  are able to hold and then after how much data are actually on the hard drives. Also tell me what format you put Drive D: in, if you don't know how to tell its fine:)

---

### Post by seejay2 on 2014-02-12
Sorry, C: and D: are 500 GB each.  I don't know exactly  how much is on them right now, I just did a 'factory reset' (all may data is backed up on an external) which didn't fix the windows explorer issues.  I think there's about 45 GB of data on C: and D: is less than 1GB.  I believe the format is NTFS.  Thanks.

---

### Post by Votlon on 2014-02-12
*Also is C: drive now fixed?

Okay, from the sound of it you really don't need a dual boot unless you really want to. I would keep One of your hard drives as windows and make the other pure Ubuntu.
And if you ever need files from your windows computer you just *Nautilus *your way into your windows files. (Nautilus is the file explorer for Ubuntu) 
And if it is an issue that you need a extra partition just for files i would do it on your C: drive that has only windows and just make a 200gb partition for data.

---

### Post by Odyssey1942 on 2014-02-12
dallen, From what the OP said, I think that he does not know how to implement your suggestion. Perhaps more specific suggestions with examples would be helpful?

---

### Post by mastablasta on 2014-02-13
let's go back a bit - are you sure these are drives and not parittions? HP puts resotre files on HP_tools partition and often ther eis also a bot partition. it's how you do "factory reset".

you can't just guess if the drive is damaged there are S.M.A.R.T. tools that will say definitly if drive is damaged or not. if onyl windows explorer is crashing it doesn't mean the drive is damaged. if it was damaged you probably wouldn't even make it to explorer.

steps: boot into ubuntu and select try it. run gparted and post picture of how your drive(s) look like. 

another option is to while in ubuntu open terminal and copy&paste this command into it: 

```
sudo fdisk -lu
```

then copy and paste the output here using code tages (the # icon)

the comand or gparted whichever way you choose will say how disk is arranged so we can advise how to create dualboot. 

and if you go into the terminal you can also copy&paste this command into it 

```
lshw


```this will list all hardware. so we can see if it's all compatible and how well will it run. alternatively there should be a system info applicaiton. i am not sure what it's named in Ubutnu as i use Kubuntu. you can also get system specs info there.

---

### Post by G_Ajith_Kumar on 2014-02-13
Hi,   I have an HP Laptop too. Compaq Presario C-301.. much older basic model. I used Windows7 till a month back, dual boot for about a week there after and then switched over totally to Ubuntu. I do not need to have Windows any more since Ubuntu takes care of all my needs!!!! :)

To my mind, the fact that you are booting in to Windows means that basically there is no major issues with Window Installation as such. There seems to be a problem with the explorer and that could probably be fixed. In the mean time may be you could try out Ubuntu and then decide what to do there after ---a dual boot or only one OS. You have plenty of hard disc space and so dual boot does not appear to be a problem at all. :)

i have checked out the specifications of your laptop. [http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c01896913](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c01896913)

It says you have a 500 GB hard disc. So are you sure you have two 500GB hard discs??? or Is one an external disc? this matters as it would indicate if your C: and D: drives are separate drives or a single drive partitioned in to two by Windows. You can still dual boot even with a single 500 GB disc partioned in to two. So no hassles about it.

To Try / Install Ubuntu you would first need to download Ubuntu, make a DVD/CD of it and then install. For that you could do the following;
      
       link for downloading Ubuntu 12.04 [http://releases.ubuntu.com/precise/u...ktop-amd64.iso]("http://releases.ubuntu.com/precise/ubuntu-12.04.4-desktop-amd64.iso")
       link for making a DVD?CD  [http://www.ubuntu.com/download/deskt...dvd-on-windows]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows")
       link for running Ubuntu from a CD [http://www.ubuntu.com/download/deskt...re-you-install]("http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install")
       link for configuring BIOS [http://www.wikihow.com/Set-Bios-to-Boot-from-a-CD-ROM](http://www.wikihow.com/Set-Bios-to-Boot-from-a-CD-ROM)

Do give a feed back and when you have solved the issue, you may mark this SOLVED.
Good Luck!!

---

### Post by Youri_van_Dijk on 2014-02-13
> **seejay2 said:**
> The computer came with no discs and I do not have a recovery disc.  Is it possible to use C: to get Windows running on D: and then do a dual-boot with Ubuntu? 
 
Thank you.

Hey Seejay you are up for quite a task, similar to the others I think the issue might not be your disk. Have you succeeded in reinstalling windows? If not, would you be able to burn a DVD? You can download the official version of windows straight from their website. I'm not sure about your exact version, but this page has a list: [http://techverse.net/download-windows-7-iso-x86-x64-microsofts-official-servers/](http://techverse.net/download-windows-7-iso-x86-x64-microsofts-official-servers/)

Try to download the image and burn it to a dvd. With it you should be able to do a clean installation of windows that might solve your problem. On the bottom of your laptop you should find a windows sticker with the appropriate licence codes you'll need during installation. 

If you can't manage to perform these steps due to the crashing behaviour you might want to install the dual boot with Ubuntu. Again I'm hoping your current windows installation might allow you to at least do some things. Otherwise the procedure gets more difficult. Please mention this and we could help you with that as well.

As your data is backed up you should install Ubuntu on d. Now for the steps.

1. Due to your inexperience you might want to download the Ubuntu installer for windows. [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)
Following the steps you should be able to install Ubuntu on d:. It will create the dual boot for you.

2. When you have installed Ubuntu, try to access the terminal (Google how to) and enter the code that was mentioned before. 'sudo fdisk -lu' and as said place the output on the form here. Only then people are able to indicate whether the disk is damaged.

3. For windows. Try to download the official windows 7 again from the Microsoft site, burn it and try to reinstall windows. I'm not sure if it will give you the option to choose the drive. It might remove the dual boot and make Ubuntu inaccessible, but when windows is reinstalled you might want to follow the procedure to install Ubuntu again. Only one way to find out. Hope this helps ;)

---

### Post by mastablasta on 2014-02-13
> **Youri_van_Dijk said:**
> 1. Due to your inexperience you might want to download the Ubuntu installer for windows. [http://www.ubuntu.com/download/desktop/windows-installer](http://www.ubuntu.com/download/desktop/windows-installer)
Following the steps you should be able to install Ubuntu on d:. It will create the dual boot for you.




wubi is not supported anymore. it's messy anyway installing ubutnu into a virtual disk inside windows NTFS system, if there is something wrong with the fuile system (malware) you might get errors.

first thing user needs ot do before install is to get it to run in live OS mode (try it).

---

### Post by seejay2 on 2014-02-19
Apparently I was feeling mildly ignorant when I posted this.  I meant that the C: drive was corrupted so I could not create an install disc and nothing I used was able to repair it.  I was also asking about how to clone the C: onto the D:, but couldn't think of the correct way to word it.  Anyway, I was not able to clone it due to the corrupted Windows files, so I scrapped the C: drive and did a clean install on the D: and was able to reinstall Windows (without all of the crap bloatware, which is a nice bonus).  Luckily, just 2 days before the C: failed I backed up all of my files to an external hard drive, so I came out of this with 0% data loss, I'm just out a week of my time trying to figure this out.  

I have done a dual-boot ubuntu install and am figuring out how it works.  So far it's great, just getting used to a new OS.  Once I figure out how to do everything in Ubuntu that I do in Windows, I am planning to dump Windows for good.  Thanks all for your comments!

---

