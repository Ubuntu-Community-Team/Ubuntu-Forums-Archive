---
title: "I can't get NDISwrapper working for me. Argh!"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-08-23
Device is a Linksys WPC54G wireless PCMCIA card.

I can get as far as Xubuntu seeming to recognize that the card is there (when I click on the Network Manager applet on the panel, "Wireless Networks" shows up, but no actual networks are there to select, even though I know there's one available because I'm using it right now), but no farther. I don't know what to try from here. The card works, the computer is working fine...

?!?!

Any help is very much appreciated. I've been trying to fix this for upward of a week now!

---

### Post by doctorbighands on 2008-08-23
It took me until right now to realize that I'm trying to use a Vista driver. No WONDER it isn't working!

I'm so ashamed...

I'm going to try installing an XP driver and see if that doesn't improve things.

---

### Post by doctorbighands on 2008-08-23
Nope...still nothing. It's still telling me that there aren't any networks within range, when there's one within 50 feet of me.

---

### Post by SubCool on 2008-08-23
i'd like to know too~

---

### Post by bobnutfield on 2008-08-23
I have read in other forums that some have had to blacklist the installed broadcom driver included in the kernel when using ndiswrapper with this chip.  When you type:

> sudo ndiswrapper -l

does it give you the name of any alternate drivers?

---

### Post by SubCool on 2008-08-23
> **bobnutfield said:**
> I have read in other forums that some have had to blacklist the installed broadcom driver included in the kernel when using ndiswrapper with this chip.  When you type:



does it give you the name of any alternate drivers?

no, and i dont have internet to it to do any synap'

---

### Post by bobnutfield on 2008-08-23
I did not mean an alternate driver to use with ndiswrapper.  I meant that some of the Linksys chips have broadcom chips and the kernel sometimes loads a conflicting driver which would need to be blacklisted if it was conflicting with the windows driver loaded with ndiswrapper.  Try doing sudo lsmod to see if there is a broadcom 802.11 module listed.  If there is, try blacklisting it.  This has happened to me in the past when a  kernel driver conflicted with ndiswrapper.  If there is no broadcom (bcmw, or similar) listed, then try to note any other 802.11 drivers other than ndiswrapper that might be listed.

---

### Post by doctorbighands on 2008-08-23
> **bobnutfield said:**
> I have read in other forums that some have had to blacklist the installed broadcom driver included in the kernel when using ndiswrapper with this chip.  When you type:



does it give you the name of any alternate drivers?

It DOES give the name of an alternate driver! Competing drivers makes perfect sense. How do I go about blacklisting?

Less than an hour, and already my thread is hijacked. That must be some new record! :)

---

### Post by bobnutfield on 2008-08-23
Note the name of the driver that is shown as an alternate driver, and type:

> sudo rmmod <nameofdriver>

Then go to /etc/modprobe.d/blacklist and add the name of that diver to the end of that file.  You will have to use gksudo to edit the file and save.

Then, reboot with ndiswrapper loaded.  If you do not have it listed in /etc/rc.d/local so that it loaded at boot, after you have reboot with the kernel driver blacklisted, just do modprobe ndiswrapper again.

---

### Post by SubCool on 2008-08-23
> **doctorbighands said:**
> It DOES give the name of an alternate driver! Competing drivers makes perfect sense. How do I go about blacklisting?

Less than an hour, and already my thread is hijacked. That must be some new record! :)

;-)

im trying it now. So far no go- 
The Module in lsmod was a b43. I am seeing some conflicting advice on how to fix this. Im kinda scared to fix this.

---

### Post by bobnutfield on 2008-08-23
You are not going to do any harm blacklisting the b43 driver just to see if it get ndiswrapper working for you.  If it does not work, simply to to /etc/modprobe.d/blacklist and remove it from the file and save.  You are not removing that driver from the kernel when you blacklist it, you are simply keeping it from automatically loading at boot.

I do not know what other advice you are being given, but if something else works, then great.  This is simply how I have solved the problem of conflicting drivers with ndiswrapper in the past.  No guarantee it will work for you.

---

### Post by doctorbighands on 2008-08-23
Blacklisting the extra driver worked like a charm!!! Thank you ten billion times over!!

The only issue remaining is that each time I reboot, I have to open a terminal and modprobe in order to get the card working again. Is there a way to get Xubuntu to do that automatically at startup?

---

### Post by bobnutfield on 2008-08-23
Yes you can type the command modprobe ndiswrapper in a file called/etc/rc.d/local (I believe that is the location in Ubuntu. I sometimes confuse that file because I use so many distrobutions.)  By placing the command in that file, it will automatically be run when you reboot.

---

### Post by doctorbighands on 2008-08-23
In the /etc directory, there isn't a folder called "rc.d". Instead, I have rc0.d, rc1.d, rc2.d, etc. I can't find a file called "local" inside any of those.

I am using Xubuntu, which is probably the difference. Any idea where I might find that "local" file in XFCE?

---

### Post by bobnutfield on 2008-08-24
Sorry, time differ ence here.  The correct folder is /etc/init.d/rc.local.

---

