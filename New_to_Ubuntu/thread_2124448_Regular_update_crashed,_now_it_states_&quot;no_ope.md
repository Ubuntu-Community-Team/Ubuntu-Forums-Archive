---
title: "Regular update crashed, now it states &quot;no operating system found&quot;."
date: 2013-03-11
forum: New to Ubuntu
---

### Post by bolgre11 on 2013-03-11
Hey everyone, 

As my first totally linux system, i've been running lubuntu 12.04 on a lenovo x120e with an OCZ vertex 60gb SSD switched out in place of the stock HDD for some time now with no major problems (other than the wifi card, but i've read that is pretty standard with this setup). The other week I was in the middle of a typical update when it said that there was an error with the program. I exited out of the window and noticed that my background was totally black, and my desktop icons weren't visible. I (with little forethought) decided to reboot, at which point I was unable to even get GRUB to load. The computer reaches its initial startup screen after the lenovo logo appears, at which point it states "No boot filename found, exiting PXE MOF." The screen then goes totally black for several moments before simply stating "No operating system found." I have to hold down the power button for a hard shutdown to get the computer to leave this screen. 

After researching for similar problems, I came across the boot-repair program, and thought this could help. I loaded the ubuntu secure remix that contains it onto a live usb and ran the diagnostic, which stated that my boot was successfully repaired. The same sequence I described above still happens upon startup. [Here]("http://paste.ubuntu.com/5559859/") is the pastebin log of the occurence. 

As of right now, the only way I can use my computer is while using a live usb. 

Normally i'd just wipe the system and do a fresh install because I back my data up weekly and try not to keep a whole lot stored on the actual HD, but there's a few important pieces of academic work I can't afford to lose that were only on the HD during the fated week in question. With the quarter coming to a close, that work is becoming more and more necessary to have. 

If there's any advice you all could offer to help me at least recover the data, let alone restore the system, i'd be incredibly grateful. 

Thanks!

---

### Post by carl4926 on 2013-03-11
Boot to the live session, using the same media that you installed with.

 * Open a terminal and type


```
sudo fdisk -l

```

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt


```
sudo mount /dev/sda1 /mnt

```

    * Now mount the rest of your devices


```
sudo mount --bind /dev /mnt/dev

```

    * Now chroot into your system


```
sudo chroot /mnt

```
Now lets try updating things with

```
apt-get update && upgrade
```

```
update-grub
```
```
grub-install /dev/sda
```

then reboot

---

### Post by bolgre11 on 2013-03-11
That makes total sense, thank you for spelling it out in such a way!

For clarification, if I do not have the original media that I installed with, would it be acceptable to create another live usb with the same version of lubunu on it?

---

### Post by carl4926 on 2013-03-11
> [COLOR=#000000]For clarification, if I do not have the original media that I installed with, would it be acceptable to create another live usb with the same version of lubunu on it?[/COLOR]
Yes
Same version and arch
ie: 32 or 64 bit - whichever you used

---

### Post by Bucky Ball on 2013-03-11
> **carl4926 said:**
> 
Now lets try updating things with

```
apt-get update && upgrade
```

```
update-grub
```
```
grub-install /dev/sda
```



These commands should also have 'sudo' preceding them. ;)

---

### Post by carl4926 on 2013-03-11
> **Bucky Ball said:**
> These commands should also have 'sudo' preceding them. ;)

Should not be needed when you are chroot

---

### Post by Bucky Ball on 2013-03-11
> **carl4926 said:**
> Should not be needed when you are chroot

Of course. My mistake. ;)

---

### Post by bolgre11 on 2013-03-15
Thanks again for your explanation, but it looks like i've hit a snag in the process. I managed to get the proper live usb made up this morning, and upon loading it and typing in the first command you listed, I only get an output for the live usb itself. There are no other devices listed.

---

### Post by ManamiVixen on 2013-03-15
It sounds like the drive died. After a bit of reading, there are apparently cases of OCZ Vertex drives just spontaneously spazzing out or outright dieing. Contact OCZ and see if they can fix it.

---

### Post by bolgre11 on 2013-03-15
I had been reading more into that prospect the other day, I just thought i'd pray for the best. Do you know of any troubleshooting tactics I could employ before I RMA? Retrieving that data in any way would be immensely helpful to my current academic situation.

---

