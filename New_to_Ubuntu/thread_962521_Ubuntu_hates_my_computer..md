---
title: "Ubuntu hates my computer."
date: 2008-10-29
forum: New to Ubuntu
---

### Post by aaron101 on 2008-10-29
Hi,

I've tried 3 different ubuntu discs and none of them work. Two different versions, 64bit & 32bit 7.10 and the 64 bit 8.04.

Both versions of 7.10 used to give the kernel panic error and the 8.04 version either loads up a screen of a heron (or something?) and freezes or just shows a black screen and freezes.

I setup the partition with Gparteds live CD and made sure to burn the ubuntu discs at 4x speed. Also, just to mention, Fedora 9 & Mandriva One have also failed to install, well, started the install process with errors.

Can someone explain to me why I'm having such problems installing Linux? The only time I've had success is installing openSUSE 11.0 but I really want to try another distro. Help!

---

### Post by mkvnmtr on 2008-10-29
For someone to help you will probably need to give all the specs of your computer and tell step by step what happened when you tried to install. Sometimes it is very simple to make it work and sometimes it can entail several tries.

---

### Post by starcannon on 2008-10-29
Lets have a look at your computer hardware list.

If you can run the liveCD then post the output of :
```
sudo lshw
```

If the liveCD won't even boot, then using Windows or what ever means you have, give us a list of your computer hardware:
Motherboard/Chipset
CPU
RAM
Sound Card/Integrated Sound Chipset
Video Card/Integrated Video Chipset
Network/Modem
Monitor

Make and Model would be good as well.

GL and have fun.

---

### Post by aaron101 on 2008-10-29
Just been looking around the forums and noticed someone mentioning the F4/F6 options on the Live CD menu and knew exactly what I should have done. Turn the friggin ACPI off. I remember doing the same for openSUSE. And voila! Currently installing Ubuntu... 50% and ok so far!

I'll be back if I have any other problems, but I have 2 more questions.

1. What is ACPI and why is it such a problem when I try to install a Linux distro?

2. I'm using a computer which has a AMD Athlon 64... does this make it a 64 bit machine?

Thanks :)

---

### Post by NewJack on 2008-10-29
First off, after you downloaded Ubuntu did you check the hash value of the .iso?  You can check the hash list here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

Intrepid's hashes will be added on the day of release.

Second, what speed did you burn your .iso's at.  It has been recommended to burn at x4 speed.  I have always burned at x4 or x8 speed and have never had a problem with any version of Ubuntu.

Hope that helped you.

---

### Post by tarps87 on 2008-10-29
> **aaron101 said:**
> Just been looking around the forums and noticed someone mentioning the F4/F6 options on the Live CD menu and knew exactly what I should have done. Turn the friggin ACPI off. I remember doing the same for openSUSE. And voila! Currently installing Ubuntu... 50% and ok so far!

I'll be back if I have any other problems, but I have 2 more questions.

1. What is ACPI and why is it such a problem when I try to install a Linux distro?

2. I'm using a computer which has a AMD Athlon 64... does this make it a 64 bit machine?


1) Advanced Configuration and Power Interface, I believe is allows an OS to control the power management of the computer but that all I know about it

2) Your computer is a 64bit

> **aaron101 said:**
> 
kernel panic error 
It doesn't hate you it's just frightened :)

---

### Post by xpod on 2008-10-29
This might help with the various boot options.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Failing all else you could try using an Alternate cd.

---

### Post by aaron101 on 2008-10-29
> **tarps87 said:**
> 1) Advanced Configuration and Power Interface, I believe is allows an OS to control the power management of the computer but that all I know about it

2) Your computer is a 64bit

Thanks for clearing that up, I was postive my pc was 64 bit but after having a hard time installing thought maybe it wasn't!

> **tarps87 said:**
> It doesn't hate you it's just frightened :)

Haha :-D

Am using Ubuntu now with no problems, really impressed by it's wireless abilities.

---

### Post by Therion on 2008-10-29
I would try the Alternate CD first.  If that's still a no go, I'm going to suggest something that might sound a little odd, but it's what got me over a similar hump some time ago.  This assumes your CD/DVD drive is not SATA.

Take a look at the ribbon cable that connects your CD/DVD drive to your motherboard.  I'm betting it's a standard-issue 40 wire, 40 pin connector, right?  If so, go to you local PC Parts Warehouse and pick up an **80 wire** 40 pin connector.  I know it might sound daft, but I'm not joking.  My optical drive was giving me all kinds of fits until changed out the cable to one with 80 wires.  

I have been told that the additional wires (that don't connect to anything) help isolate the signal and eliminate noise that you have with standard 40-wire cables.  For things like listening to music CD's a little noise is tolerable, but when it comes to pushing serious amounts of data (like when you're using a LiveCD) the noise becomes an issue.  All I know is it worked.  The cable set me back about $8.  

Free bonus pic:  [40 wire vs 80 wire](http://geekspeak.org/articles/hard_drive_technologies/40wire_vs_80wire_800x653.jpg) cables compared.

---

### Post by dracayr on 2008-10-29
> Am using Ubuntu now with no problems, really impressed by it's wireless abilities.

*lol* Wireless is rather the weak point of ubuntu or linux in general. you're lucky it worked out of the box for you.

dracayr

---

### Post by aaron101 on 2008-10-29
> **dracayr said:**
> *lol* Wireless is rather the weak point of ubuntu or linux in general. you're lucky it worked out of the box for you.

dracayr

Haha, I was pretty surprised to connect to the internet so quickly as well :o

And to Therion - I'll check that ASAP. I've had problems like that before on other computers, but didn't think to check it.

---

