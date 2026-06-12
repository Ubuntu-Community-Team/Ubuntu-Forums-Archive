---
title: "Auto Power On"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Nikunj93 on 2008-05-12
Need a software for automatic power on of PC at a scheduled time
I know a software for that in windows its AUTO POWER ON & Shutdown
want that for ubuntu

I read somewhere it can be done through BIOS but i dunno how :(

---

### Post by Six_Digits on 2008-05-12
You could use Advanced Power Management to shut-down but I don't know anything offhand for start-up.

```
sudo apt-get install apmd
```

---

### Post by saj0577 on 2008-05-12
Not exactly what you want but take a look at WOL (Wake ON Lan)

Saj

---

### Post by okey666 on 2008-05-12
My BIOS gives me options. Take a look by pressing F1/F10 (depending on your system) while it is doing the memory checks etc, (loads of black/white text before Ubuntu starts)

When it is doing the memory checks it may tell what key to press.

---

### Post by Nikunj93 on 2008-05-12
i go to BIOS then Power Managment System
After that
i see
Something
PME
and
Alarm
is these the things i need?

---

### Post by Nikunj93 on 2008-05-12
anyone please reply

---

### Post by mostafakvd on 2009-03-25
We are both in the same boat I was working with Auto power on and shutdown in windows as well but since I traveled to linux I can't
It is obvious for me that linux developers can solve this problem but when I don't know :( 
But I wish they could solve it as soon as they can.
I will appreciate any ones help

---

### Post by CatKiller on 2009-03-26
> **mostafakvd said:**
> It is obvious for me that linux developers can solve this problem but when I don't know :( 

Not really. Pretty obviously, when the computer is turned off Linux isn't running. There isn't any way that it could be.

Some computers (strictly, some motherboards) have the ability to turn themselves on at a particular time. Most don't. If your computer is capable of doing so, there will be an option in the BIOS to tell the computer when you want it to turn itself on. If there's no option there, then your computer can't do it.

Similarly, some network card/motherboard combinations are able to turn the computer on when the network card receives a magic packet that tells it to turn the computer on. Many don't, and some need a special cable that goes from the network card to the motherboard. This system is called Wake-on-LAN, and was mentioned earlier. This system lets you turn your computer on remotely over the network from another computer. If your computer is capable of doing this, then it is quite straightforward to set up. But again, your computer might not be capable.

If your computer isn't capable of being turned on by either of these methods then you either need to press the button yourself or get a more capable computer. No amount of complaining about it can change this simple fact.

---

### Post by blau2009 on 2009-03-26
> **Nikunj93 said:**
> i go to BIOS then Power Managment System
After that
i see
Something
PME
and
Alarm
is these the things i need?

AFAIK, alarm would be setting a particular time each day for the PC to turn on. So you could set it to 8.50am so it would be ready for work at 9am.

PME is more complicated but can be controlled by software. For example if you were setting up a PVR box and wanted to set it to turn on when a show is scheduled to be recorded you could do so.

There are of course many variations and it's not generally something that is included in desktop motherboards, because not many people use it. If your PC has those options in the BIOS, I would think it would be possible. Sorry but I don't know of any specific applications to do so.

I guess the main point is, why do you want to turn on the PC unattended?

---

### Post by freak42 on 2009-03-26
you can set auto wakeup on some motherboards w/ linux, it is discussed in depth here: [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup) albeit in a slightly different setup. but maybe this is a starting point?

hth

---

### Post by kalug on 2009-10-03
Hi all,

I faced recently the same problem described here... I have an MS-1221 motherboard and in BIOS there is no such entry like APM... Does this mean that there is no way I can make my notebook to wake-up from for example hibernation?
I also tried to setup nvram-wakeup in ubuntu but the produced .conf- file contianed only:

################################################
##  Mainboard autodetection information:
##
##    - Mainboard vendor:   "MSI"
##    - Mainboard type:     "MS-1221"
##    - Mainboard revision: "Ver 1.000"
##    - BIOS vendor:        "American Megatrends Inc."
##    - BIOS version:       "A1221IMS V3.5"
##    - BIOS release:       "03/10/2009"

---

### Post by DalaiDakkar on 2010-11-16
On windows there's a way to turn on the computer but I actually don't know how it works if someone could clarify would be great, so this is how it works, you need to have your windows hibernate instead of poweroff, then on the task scheduler for windows you add a new entry, let's say run the calculator at 2.00 am then you hibernate your PC and ZALOM!! it turns on at 2.00 am, I use this for torrent download then you can add another job with the right command to hibernate again at 9.00 am (I use this for nightly torrent downloads on a windows machine) and I was asking myself if this could be achieved in linux but really since the hibernation in linux it's barely supported I don't think there's an alternative other than scheduling the wakeontime on the bios of the motherboard. If anyone know how windows can turn itself on please explain.  Thanks in advance!

---

### Post by freak42 on 2010-11-16
There are at least some hardware configurations where it is in fact possible to put Ubuntu into Suspend mode and wake up from it. I know because I have done it for my Mythbuntu Box (on an old Dell Inspiron Laptop).
However it wasn't a pleasant experience to setup and test, and the procedure really depends on the underlying hardware. It's been a great while since I have done there I already forgot the specifics, however I suggest you head over to the mythbuntu wikis, tutorials and forums as this topic is sometimes discussed there.

hth

Matthias

---

### Post by Blutkoete on 2010-11-16
Just to put some things straight: [Auto Power On & Shut Down]("http://www.lifsoft.com/") doesn't turn on your computer. It's only capable of starting it up from either hibernation or sleep mode on a specific time.

Maybe there's a Linux tool that covers that, as the system is kind of running during hibernation and/or sleep mode.

---

### Post by Lt_Worf on 2011-10-13
There's a package called nvram-wakeup. It does not support all the BIOSs existing, so in some case it can't help you but give it a try.

I am disappointed to see MANY people replying and none of them taking the time to do an "apt-cache search".

---

### Post by oldos2er on 2011-10-13
Closed, necromancy.

---

