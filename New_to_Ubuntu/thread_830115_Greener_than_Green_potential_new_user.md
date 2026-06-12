---
title: "Greener than Green potential new user"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by FroggyZ on 2008-06-15
Peace be unto you all!
I need help in liberating myself from King Gates.

I want to try UBUNTU by installing it on my external hard drive and running it from there.

I only have one computer & I'm afraid of installing another OS there and losing everything from a lack of knowledge.

I would love to plug in my external drive, run UBUNTU from it and go about my business w/o there being a "foot-print" on my computer.

Ultimately, I would like to have everything on the external, go to my other office, plug in my external, use UBUNTU, do my work, then return home.

Am I dreaming?

I have a Western Digital 250 GB Passport external HD

Thanks in advance for your input.

FroggyZ:guitar:

---

### Post by cprofitt on 2008-06-15
As long as you can boot to the external USB device you should be ok... the tricky part will be having Ubuntu not over-write your boot loader on your Windows drives (you could disconnect them to be sure).

---

### Post by dnns123 on 2008-06-15
If you know how to change the boot priorities in the BIOS, then your good to go!

---

### Post by mikewhatever on 2008-06-15
It's a bit more complicated two have two HDDs with OSs, because GRUB boot loader for Ubuntu sometimes gets confused, but is quite possible, nevertheless. One important thing to check before you start is whether or not your computer can boot from USB.
Click [HERE]("http://www.google.co.il/search?hl=iw&client=firefox-a&rls=org.mozilla:en-US:official&hs=p8a&sa=X&oi=spell&resnum=0&ct=result&cd=1&q=ubuntu+installation+external&spell=1") for links.

---

### Post by fiddledd on 2008-06-15
Firstly download the LiveCD and check it recognizes all your hardware. Then have a read here [http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/](http://www.belutz.net/2007/04/13/installing-ubuntu-on-external-usb-hdd/)
Apparently it all went OK.

---

### Post by Dr Small on 2008-06-15
> **PrivateVoid said:**
> As long as you can boot to the external USB device you should be ok... the tricky part will be having Ubuntu not over-write your boot loader on your Windows drives (you could disconnect them to be sure).
There is nothing tricky about it. Unplug the Internal Harddrive, and then install to the External drive.

---

### Post by FroggyZ on 2008-06-15
> **Dr Small said:**
> Unplug the Internal Harddrive, and then install to the External drive.

Can't do that at work, could get fired for opening the company's computer.
What else?

---

### Post by waspbr on 2008-06-15
hmmm, provided you have enough space in your windows partition, if you just wanna try it, I would recommend you make a small wubi install on whatever computer you wanna use.

If you haven't heard of wubi it basically is a windows ubuntu installer, that installs ubuntu as a program on a virtual partition. If you don't like it just go to windows control panel and uninstall it. It is slightly slower than what a real ubuntu install would be but it is nice for trying out.    

wubi comes in all hardy (ubuntu 8.04) lice CDS, just pop it in while you have windows on and happy hunting.

---

### Post by fiddledd on 2008-06-15
I'm not sure if this might be what you want, have a look here:
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

This is for 7.10 Gutsy though, not Hardy.

---

### Post by Martje_001 on 2008-06-15
> **FroggyZ said:**
> Can't do that at work, could get fired for opening the company's computer.
What else?
Can you do it at home? Or don't you own a computer at home? Then you can ask a friend..

---

### Post by waspbr on 2008-06-15
If you really wanna do the usb thing, I found this link

[http://netpatia.blogspot.com/2008/02/install-ubuntu-on-usb-stick.html]("http://netpatia.blogspot.com/2008/02/install-ubuntu-on-usb-stick.html")

---

### Post by FroggyZ on 2008-06-15
So, what I'm hearing is that I would have to disconnect the hard drive on my or what ever computer I'm on to use UBUNTU from an external HD or ditch Windows altogether and go straight UBUNTU.

Doesn't look like there's a happy medium here.

Complicated registry changes which, if not done correctly, could damage my PC.

Let me restate my objective.
[LIST]
[*]Install UBUNTU on external hard drive.
[*]Take external drive with me.
[*]Plug it into the USB port of whatever computer I'm using (without opening the box to disconnect something).
[*]Use UBUNTU
[*]Remove external HD w/o damaging the "host" computer.
[/LIST]

Is this possible?

If not, I'll just hang on to Gates until somebody figures out how.

THANX!

---

### Post by FroggyZ on 2008-06-15
From what I've read so far, my objective of a stand alone external USB drive with UBUNTU on it to be run from any PC I plug into is a pipe dream. Especially for those of us that don't have a Phd in programming or have only been exposed to Windows environments.

I feel like a brick layer in a dentist's convention with some of the answers I've gotten. Sorry I don't speak Linux. What I really need a "DUMMIES" manual written to a true novice without the "computerese" that wants to move up.

FroggyZ:guitar:

---

### Post by esteckis on 2008-06-15
The reason some instructions ask you to disconnect your in case hard drive is to avoid accidentally loading the Grub boot loader onto that hard drive (but you really don't have to disconnect your case hard drive if you are careful enough). But here is a link with some pics. [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/")

# 9 on the link above is the critical thing.
The thing you will have to do is download the UBUNTU live cd and burn and run it as a live session. Use the  partitioner  to view what each hard drive is labeled so that when you go to install Ubuntu with the grub bootloader, you can tell the install which hard drive to install the boot loader onto.

But I also suggest you get the Super Grub Disc (download and burn it to a cd. The first time I tried Ubuntu (newbie) I installed it onto an external USB hard drive and then later on  when I disconnected my usb HD I was unable to boot to windows because I did not know that Grub was installed to the c drive. The Super Grub Disc has an option to correct your boot loader in case this happens.

Also just another note. This website also shows you how to install all sorts of different flavors of Ubuntu on to flash drives.

Also another item I use  is this link [http://portableapps.com/]("http://portableapps.com/")
"Now you can carry your favorite computer programs along with all of your bookmarks, settings, email and more with you. Use them on any Windows computer. All without leaving any personal data behind."

Now these are modified programs that run on a USB (or can be on usb hard drives also). These are set up for portability and with no registry entries. There is a big listing of software. Alas, you have to have windows running on the computer to run these programs.

---

### Post by wannadumpwindows on 2008-06-15
> **FroggyZ said:**
> From what I've read so far, my objective of a stand alone external USB drive with UBUNTU on it to be run from any PC I plug into is a pipe dream. Especially for those of us that don't have a Phd in programming or have only been exposed to Windows environments.

I feel like a brick layer in a dentist's convention with some of the answers I've gotten. Sorry I don't speak Linux. What I really need a "DUMMIES" manual written to a true novice without the "computerese" that wants to move up.

FroggyZ:guitar:

It's perfectly possible. The only time they're suggesting you unplug the internal drive is on the initial install on your external.
 
P.S. You can also do it on a USB thumb drive, if you ever decide you want linux in your pocket. It's exactly the same steps either way.
You won't need to unplug them just to run it. It'll work perfectly fine. You just have to watch where you install grub. 
Other than that, it should be easy as pie.

You should be able to get EXACTLY what you want, all the info you need is already here.

---

### Post by JoshuaRL on 2008-06-15
> **FroggyZ said:**
> So, what I'm hearing is that I would have to disconnect the hard drive on my or what ever computer I'm on to use UBUNTU from an external HD or ditch Windows altogether and go straight UBUNTU.

Doesn't look like there's a happy medium here.

Complicated registry changes which, if not done correctly, could damage my PC.

Let me restate my objective.
[LIST]
[*]Install UBUNTU on external hard drive.
[*]Take external drive with me.
[*]Plug it into the USB port of whatever computer I'm using (without opening the box to disconnect something).
[*]Use UBUNTU
[*]Remove external HD w/o damaging the "host" computer.
[/LIST]

Is this possible?

If not, I'll just hang on to Gates until somebody figures out how.

THANX!

Perfectly possible.  The reason it was suggested that you disconnect the internal Hard Drive is that it is by far the easiest way to do what you want.

If both your work and home computers can boot from USB, it shouldn't be too hard.  Follow the steps below to do this from home:

[list][*]Turn off the computer[*]Open the case on the computer[*]Disconnect your internal hard drive[*]Plug in the external USB hard drive[*]Put in the Ubuntu CD/DVD[*]Start the computer[*]Make sure BIOS is set to load from the CD drive[*]Install to the external USB hard drive[*]Shut the computer down and connect the internal hard drive[/list]

Now when you're at work, just change the BIOS settings to boot from USB and you should be able to load Ubuntu without hurting anything.

> **FroggyZ said:**
> From what I've read so far, my objective of a stand alone external USB drive with UBUNTU on it to be run from any PC I plug into is a pipe dream. Especially for those of us that don't have a Phd in programming or have only been exposed to Windows environments.

I feel like a brick layer in a dentist's convention with some of the answers I've gotten. Sorry I don't speak Linux. What I really need a "DUMMIES" manual written to a true novice without the "computerese" that wants to move up.

FroggyZ:guitar:

Don't worry about it, just keep trying to learn and say so when something goes over your head.  We all start from somewhere, so there's no reason to feel stupid just because you don't know something.  That's why we're here.

Welcome to Ubuntu!

---

### Post by stalkier on 2008-06-15
> **FroggyZ said:**
> Can't do that at work, could get fired for opening the company's computer.
What else?

Hoenstly I would just LiveCD the OS and save files needed to an external hdd or thumbdrive. Much safer and a lot easier to do.

---

### Post by Dr Small on 2008-06-15
The biggest problem by far of installing Ubuntu on a external hard drive at home, and then plugging it in at work could be that X would break, if the two computers use different types of video cards.

That in itself would be trivial to fix.

---

### Post by JoshuaRL on 2008-06-15
> **Dr Small said:**
> The biggest problem by far of installing Ubuntu on a external hard drive at home, and then plugging it in at work could be that X would break, if the two computers use different types of video cards.

That in itself would be trivial to fix.

Especially with Hardy.  Doesn't it autodetect on bootup now instead of relying on xorg.conf?  I thought that was one of the big changes to Xorg this time, moving to autodetection instead of config files.

If you were really worried about it, you could always just install with the vesa driver and then change it to what you needed on the work computer.

---

### Post by Dr Small on 2008-06-15
I have no clue. I have only booted Hardy once from the LiveCD, so I don't know much about the new specs with it. In the olden, golden days, one could simply edit the Xorg file for the vesa driver, but if as you say, it may be simpler yet.

---

### Post by JoshuaRL on 2008-06-15
Yeah dude, it's different.  I cut my teeth on manually editing xorg.conf to get a workable system;  I feel nostalgic for Gutsy.  You might try booting the Hardy LiveCD and looking at it's xorg.conf.  It's crazy different.  I'd give you a sample of mine, but I'm stuck at work right now on XP.

---

### Post by FroggyZ on 2008-06-16
**[SIZE="4"]Huh?![/SIZE]**
"versa driver"
"Hardy"
"xorg.conf"

Parlez-vous français? 

It's all French to me.
What happened to the "absolute beginner talk?"

Big problem: I have a laptop as my main computer, can't unplug the internal drive.
This seems to be the 1st step in almost everything I've read.

Anything else?

---

### Post by Martje_001 on 2008-06-16
Just do it. Make sure you have a Windows XP (if that's what they're running) cd with you, to recover the Master Boot Record if everything goes wrong.

Steps to recover it:
1. Put in cd
2. Choose Recovery Mode
3. Choose the existing installation
4. typ: fixmbr

---

