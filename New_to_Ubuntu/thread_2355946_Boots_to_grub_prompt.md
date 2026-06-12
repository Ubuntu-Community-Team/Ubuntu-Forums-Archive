---
title: "Boots to grub prompt"
date: 2017-03-18
forum: New to Ubuntu
---

### Post by r.howell on 2017-03-18
Attempting to put Ubuntu on another laptop. Having an issue with the second one.

Both are Ispiron 6000's running Vista

Mine booted great!
My daughter's goes to a DOS screen, Grub..

At a loss of what to do in this screen.
Can you help?

---

### Post by jeremy31 on 2017-03-18
Are any options on this screen?  If it say Ubuntu on the screen, select and press enter
[http://i.imgur.com/cH8IQah.jpg](http://i.imgur.com/cH8IQah.jpg) would be normal on my laptops except some would show a Windows option

---

### Post by r.howell on 2017-03-18
I boot hit F12, select Ubuntu 14.04 32bit and it goes to a DOS screen with the script:

grub>       And awaits a command.

> **jeremy31 said:**
> Are any options on this screen?  If it say Ubuntu on the screen, select and press enter
[http://i.imgur.com/cH8IQah.jpg](http://i.imgur.com/cH8IQah.jpg) would be normal on my laptops except some would show a Windows option

Wish I did see that screen..

Tried: Boot unbutu as the command. Now says:
Error 8: Kernel must be loaded before booting

---

### Post by yancek on 2017-03-18
If you see the grub> prompt that means the bootloader (grub) wasn't installed properly
Do you have vista still installed on the problem computer?
Which installation type option did you select?  If you see 'grub>' you have a number of options you can use and the link below describes them all in detail.

[https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-linux)

If that doesn't help, go to the site below and download boot repair to the working computer with Ubuntu and burn the boot repair software to a CD or usb and then put it in the non-working computer and boot it.  When it boots, select the option to Create BootInfo Summary rather than trying to make repairs.  Post a link to the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldos2er on 2017-03-18
Edited the thread title to be a bit more clear. I doubt if there's one byte of DOS in grub.  :)

---

### Post by r.howell on 2017-03-18
That's fine.
I was asked to run a program and report what I found. Hopefully I did this correct..

[http://paste.ubuntu.com/24203509/](http://paste.ubuntu.com/24203509/)

Looks like this one's on XP, not Vista like I thought...
Still not getting it switched over.

---

### Post by grahammechanical on 2017-03-18
This is my guess. Ubuntu is not installed. The Boot Repair report says:

```
=================== os-prober: /dev/sda1:Dell Utility Partition:DellUtility:chain
/dev/sda2:Microsoft Windows XP Home Edition:Windows:chain
```

```
1 disks with OS, 2 OS : 0 Linux, 0 MacOS, 1 Windows, 1 unknown type OS.
```


I would guess that the "unknown type OS" is the Dell restore utility. It has a command.com in its partition and if I remember correctly, command.com loads an old style Windows OS. Or more likely a Microsoft DOS OS.

Here is the issue. That machine has a BIOS settings utility with MBR partitioning. This means that we are limited to 4 primary partitions and the machine is already using 3 primary partitions.

Ubuntu needs 2 partitions. 1 for Ubuntu and 1 for swap. The Ubuntu installer should be able to use the remaining 1 primary partition allocation to create an Extended partition and in the extended partition create 2 logical partitions to install Ubuntu into. So, why is it not doing that?

You have a 40 GB hard disk that has 78,140,160 sectors and, if my adding up is correct, the disk has already allocated 78,124, 032 sectors to the existing 3 partitions. This means that there is no space on the disk for Ubuntu which needs between 8 - 10 GB minimal.

Regards.

---

### Post by yancek on 2017-03-18
Whatever you did trying to install didn't work as there is no sign of any Linux system on the hard drive.
You must have xp or earlier as the boot files shown in the output haven't been used with windows since xp.
Did you use a CD or DVD with Ubuntu to install?  If you don't want the windows any more, you could try installing again and selecting the ERase disk and install Ubuntu option.  If you have any data on the computer that you want to keep, you need to get if off before installing.

---

### Post by r.howell on 2017-03-19
Hello, So we removed the original windows and created 2 separate new "raw" partitions at about 15GB each and when I try to run the installer from CD it still goes to GRUB prompt. what else could I be missing?

---

### Post by r.howell on 2017-03-19
I'm in process of installing 12.04.4 , so far so good. Very strange I couldn't load 14.04... Work so well on the other computer..
I'll try an update once completed.

---

### Post by mörgæs on 2017-03-19
12.04 is too old to be of any value. 

Better to install X/Lubuntu 16.04.2 for old hardware.

---

### Post by r.howell on 2017-03-19
12.04.4 loaded as it should have. No issue, well short of WIFI not loaded.
Upgrading to 14.04 now. 

 3 out of 6 steps completed. So far so good.

If WIFI had come up, I probably would have stayed at 12.04.4 and looked at the difference..
This Inspiron is old and 14.04 may be too much for it..

---

### Post by r.howell on 2017-03-19
> **mörgæs said:**
> 12.04 is too old to be of any value. 

Better to install X/Lubuntu 16.04.2 for old hardware.

Well I can't find a download of this to try...
Hook me up and I will.
Otherwise don't down-play 12.04.4... It still works!

---

### Post by oldos2er on 2017-03-19
Support for 12.04x ends next month.

[http://lubuntu.net/](http://lubuntu.net/)
[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by mörgæs on 2017-03-20
Slightly off-topic: Though www lubuntu net does work and offers some contents the recommended web site is [www.lubuntu.me]("http://www.lubuntu.me") . The Lubuntu community has a problem with a domain name owner in conflict with the rest of the community so the only solution was that their main graphics designer built a new and better site.

---

### Post by gordintoronto on 2017-03-20
How much memory? Try Xubuntu 16.04 on this 12-year-old system; it doesn't have the horsepower to provide a good experience with Ubuntu.

---

### Post by r.howell on 2017-03-21
> **gordintoronto said:**
> How much memory? Try Xubuntu 16.04 on this 12-year-old system; it doesn't have the horsepower to provide a good experience with Ubuntu.

500.. slow I know...
LUbuntu I have to read up on to install.

Does XUbuntu install easy?

---

### Post by yancek on 2017-03-21
> LUbuntu I have to read up on to install.

Lubuntu uses the same installer as Ubuntu and the major difference you will see installing Lubuntu is that the backgorund color will be blue.

---

### Post by mörgæs on 2017-03-22
No, Lubuntu is the only member of the Buntu family which offers an [alternate installer]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO"). Suitable for old computers.

---

### Post by r.howell on 2017-03-22
Lunbuntu was like filling out a 30 page questionnaire.. Has to be an easier way.
Xunbubtu I did from the Terminal and setup nicely.


Xunbuntu is very slow.. I mean slower than Unbuntu 12 (.04 I think)..

I know have two identical laptops, one running Unbuntu 12.04.4, the other running Xunbuntu 16.04.2
Neither are strong enough to take the latest LTS Unbuntu, so I may just keep them on Unbuntu 12.04.4

I'd really like to try this Lubuntu, but that questionnaire killed me.
Can you also load it from Terminal? And bypass all the manual settings?

---

### Post by mörgæs on 2017-03-23
Well, then rest in peace.

If you resurrect some day then please read the link in my signature. 

The alternate ISO is only one of the installation methods that Lubuntu *offers*. Many more to choose from.

---

### Post by r.howell on 2017-03-25
After several different versions and many hours of reading, following instructions trying...
I'm back to Unbuntu 12.04.4 as the best running platform.

All others are either extremely slow or hang..

Thank you all for your help.
The old laptop is up and running again.

As far as 'grub' goes, looks like the version was either too much for the system or a bad boot disc (though I did try a stick boot as well).

Anyway, it's back and running.

---

### Post by mörgæs on 2017-03-26
Are you aware of what happens when [support runs out]("https://ubuntuforums.org/showthread.php?t=2355946&page=2&p=13622738&viewfull=1#post13622738")?

---

### Post by Geoffrey_Arndt on 2017-03-26
My impression is that Mr. Howell may not care what happens, after all, the "old laptop" still had XP running on it (. . . enough said).

However, there are a lot of yet lighter versions of Linux that could be tried such as **_"AntiX"_** which is based on Debian stable and still offer the users ongoing support and security fixes.

   [URL="http://distrowatch.com/table.php?distribution=antix"]http://distrowatch.com/table.php?distribution=antix


[/URL]

---

