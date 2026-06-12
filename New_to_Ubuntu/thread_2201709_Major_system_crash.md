---
title: "Major system crash"
date: 2014-01-25
forum: New to Ubuntu
---

### Post by bill24 on 2014-01-25
Major system crash.

Sorry if this is longish.  I’m setting up a Toshiba P305-S8915 for my wife.  We have several PCs and I usually install Ubuntu as an occasional alternate OS to Windoze 7 on each and have never had problems.  For no obvious reason my wife’s laptop crashed while in System 7.  (And a very strange crash indeed.  The computer locked, on reboot would launch Win Media Center.  Most programs were erased and the few that were remaining when clicked on would simply relaunch Win Media Center?) 

This laptop has two internal drives, I installed Ubutnu on the D drive and tried to boot from that but it only have me a “BOOTMGR IS MISSING” error message.   I tried to use the System 7 OS reinstall/recovery disks.  The process started OK, then hiccuped and that crashed.  Further attempts only gave me a “BOOTMGR IS MISSING”.  At that point I decided to simply bag anything Windows on that machine and just go with Ubuntu.  She needs to surf, do email and watch the occasional movie DVD.  I’ve tried to install Ubuntu from a pen drive and get that same “BOOTMGR IS MISSING” message.  I suspect/might it be that going to the F2 button and selecting which drive I wish to boot from doesn’t seem to work as it always seems to default to C drive. 

Now what?  Any suggestions of how to install Ubuntu as the only OS on this laptop given that the BOOTMGR has died?  I’m not terribly geeky and don’t have a clue where to start.

Bill24

---

### Post by wlraider70 on 2014-01-25
Sounds like your windows drive lets call it C: was the primary boot drive. with boot manager and when that went you tried to boot linux lets call it D: but D has not bootmanager or grub. 

Load from a live CD or USB and try something like this 
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UuQXQhAo7IU](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UuQXQhAo7IU)

it should show you have to update/setup grub.

---

### Post by bill24 on 2014-01-25
It sounds promising, but....  When I go to that page I find the first bit of instruction is, "Mount the partition your Ubuntu Installation is on. If you are not sure which it is, launch GParted (included in the Live CD) and find out."  I tried both a new DVD and my thumb drive, both of which has the current install ISO, and using either F12 or F2 does nothing.  I can do nothing to get anything other than a "BOOTMGR IS MISSING" from showing up.  What is meant by "Mount the partition your Ubuntu Installation is on."  From where do I do that, realizing that C, D, DVD or thumb drive will not be recognized?

Bill24

---

### Post by king.of.random on 2014-01-25
That is a little odd as I guess you must have originally installed from a live dvd / thumb drive. Try going into the machines bios and see what drives it is able to detect (can you do this on your laptop?). It maybe worth making sure that your dvd drive is set to boot first.

---

### Post by blackbird34 on 2014-01-25
Hi. 

If I remember right [PendriveLinux]("http://www.pendrivelinux.com/") (Windows) and Startup Disk Creator (preinstalled in Ubuntu) are 2 Live USB creation tools whose live USB  systems automatically become the first system to boot if they are plugged in (i e take boot priority). It surprised me a bit at first. Could be helpful. 
Have you tried either?

Once you do manage to boot a live Ubuntu system, install Boot Repair. A one-stop, one-click tool to repair your boot manager. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

To install: ```
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
```

```

sudo apt-get install -y boot-repair && (boot-repair &)
```

The final bit (after "&&") will start Boot-repair, look for a boot manager and create one where it should be if its not there. 

Again, all info sourced from here, where you will find more detailed help: 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by rburkartjo on 2014-01-25
if you still need to get into your bios i tap f2 when starting up my dell and goes right into bios

---

### Post by rburkartjo on 2014-01-25
and that boot repair that black noted should also work. at least it has for me. in fact i put boot repair on a thumb drive and then just boot up. if your computer is set up like mine you should be able to hit f12 and directly boot it up.

---

### Post by blackbird34 on 2014-01-25
Yep. 

More info: [http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

---

### Post by bill24 on 2014-01-25
I went into system setup and learned that I cannot access the bios from there.  I can see it, I have "Version 2.5" but cannot access it.  If in set-up, I attempt to boot from the thumb-drive I see the little lights on the thumb drive blink, if I attempt to launch from the DVD I can hear the DVD drive spin as though it were being asked to do something.  I still get the BOOTMGR IS MISSING error.  Might it be that the iso I downloaded is in error?  If I just copy that iso to the thumb-drive should that be adequate to work or do I have to do something else to "install" or "activate" it on the thumb drive?
Bill

---

### Post by bill24 on 2014-01-25
I just tried the PenDriveLinux.  Didn't work.  Just to test it, I tried it on a different System 7 machine.  Didn't work there either.  Bummer, a neat idea.

Bill

---

