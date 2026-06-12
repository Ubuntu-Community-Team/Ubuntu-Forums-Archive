---
title: "Wubi won't go, so if you know...helppppppppp...."
date: 2016-01-21
forum: New to Ubuntu
---

### Post by gordon18 on 2016-01-21
Hi guys I downloaded and installed wubi on a virtual disk. Unfortunately I didn't notice what it said about windows 8. Now I can't unmount the disk or eject it or delete it or format it, in short it just won't go. And now when I insert a disk into what was my "D" drive it says wubi removable disk "J". Its time I re-installed windows back to windows 7 as 8 is crap, but I don't want to get stuck because I can no longer find D drive if you know what I mean....Thx for all your help in advance.:D

---

### Post by leunam12 on 2016-01-21
Windows 8 is actually faster and less buggy than Windows 7, if the new interface in Windows 8 is driving you crazy just install "Classic Shell" for a Windows7 feel and look with all the advantages of Windows 8 in speed and performance.

Regarding your question, what do you mean when you say that you installed Wubi on a virtual disk? Wubi is not the right way to install Ubuntu, its use is discouraged and you won't find much support, if any. Maybe if you provide a more detailed description of what you did.

Another point is that if all you want to do is install Windows 7 from scratch all you have to do is boot from the installation media and erase all the partitions and create a new one; the installer will create one or more smaller partitions that are "system reserved" and you will be able to install  Windows on the larger partition (it will be selected by default after Windows installer creates the other partition).

---

### Post by Vladlenin5000 on 2016-01-21
Hi and welcome.

First of all you shouldn't use WUBI. Here are the [Forums Staff recommendations on Wubi]("http://ubuntuforums.org/showthread.php?t=2229766"). Please carefully read and understand.
second, your current main issue is Windows only, nothing to do with Ubuntu except for the fact it happened with a virtual drive mounted from an Ubuntu installation media image file (but could happen with any other). Keeping this in mind, I can venture an explanation: Windows or the third-party tool you used to mount the ISO doesn't allow unmounting because some process is accessing the (virtual) drive. Perhaps the installer which you started and then aborted kept some process running. You should have checked the task manager already.

That said, and sorry for being so direct, blunt, whatever..., the way you wrote your post, the wrong use of terminology and overall tone, tells me you aren't competent enough to be messing with operating systems installations. Particularly, the nuclear solution (reinstall) you mentioned seems quite over the top for such trivial issue.
Besides, if you have a factory installed Windows 8 it means:

1. You have a fairly modern machine with UEFI instead of the old BIOS;
2. Newer is recommended - Windows 10 - and not the rapidly aging Windows 7.
3. A dual boot installation or even Ubuntu as standalone may or may not be way more complex than in PCs with the old BIOS, may or may not require one or more brand/model specific tweaks/workarounds.

All things considered and before anything else there are three things you should do: Backup, backup & backup. Then it's safe(r) to fiddle with it.
Please open a thread with useful information such as your full hardware specifications and what _exactly_ you want to do - dual boot or Ubuntu alone - and we'll try to help you to achieve that goal. If however your goal now is to (re)install Windows only then please find a Windows forum as this one is NOT a free tech support for all things IT.

PS - Keep your thread title simple, short and assertive. Avoid "help" and similar childish expressions. Follow [this guidelines]("http://ubuntuforums.org/showthread.php?t=1422475") instead.

---

### Post by oldfred on 2016-01-21
If you had Windows 8 with gpt partitioning, and then installed Windows 7 in BIOS mode with MBR(msdos) partitioning you have a corrupted drive. Windows does not correctly convert from gpt to MBR, it leaves backup gpt data. Better to have converted Windows 7 to UEFI install on flash drive.

Post this, from terminal in live installer:
sudo parted -l

If dos or msdos with gpt, you can use fixparts to remove gpt data. If drive is really gpt do not run fixparts.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by grahammechanical on 2016-01-21
What is a virtual disk?

Do you mean a virtual machine (VM)? Is Ubuntu installed in a VM with Windows 8 as the host OS? I have no experience running a VM with Windows as the host and only a little experience running a VM with Ubuntu as the host. I think we delete VMs from the host OS.

Regards.

---

### Post by gordon18 on 2016-01-21
I just want to unmount the virtual disk that is now stuck on my machine and get my cd-rom back from the crapware, but thx for all your help.

---

### Post by QIII on 2016-01-21
Are you talking about an optical disk being physically stuck in your optical drive?

---

### Post by Vladlenin5000 on 2016-01-21
Please post a screenshot of the said virtual drive in the file explorer so we all know what are you talking about.

---

### Post by gordon18 on 2016-01-22
[IMG]https://flic.kr/p/CrnyU1[/IMG]ok what happened was I created a virtual machine using VMware12 on a Windows 8 machine.But now whenever I insert a disk into the cd-rom it reads the disk and says that its "wubi" as you can see from the screen shot ([https://flic.kr/p/CrnyU1](https://flic.kr/p/CrnyU1)) It also says that it is on disk "J" the removable disk. So somehow it all got messed up as I now seem to have an "E" recovery disk and no "D" disk which I had before. I want to re-install windows but am not sure now with all this mess I seem to have created. Any advice would be great and much appreciated

---

### Post by oldfred on 2016-01-22
Even though not shown on Disk, wubi is an exe file, so Windows may try to execute it if you have auto on in loading exe from DVDs.

Ubuntu should be booted from UEFI boot menu and you should get two boot options UEFI:name and just name which is BIOS boot. 

Why reinstall Windows?

---

### Post by leunam12 on 2016-01-23
If all you want to do is re-install windows, then none of this matters, just re-install it. Can you boot from the installation media? If you can you will have the option to delete all the partitions and create a new partition for Windows 7. I would clone the hard drive first in case something goes south and you want to go back.

---

### Post by hakuna_matata on 2016-01-24
> **gordon18 said:**
> as you can see from the screen shot ([https://flic.kr/p/CrnyU1](https://flic.kr/p/CrnyU1))
The timestamp "10/17/2012 6:08 PM" probably means that the files and folders are part of Ubuntu 12.10. Ubuntu 12.10 is no longer supported.

---

### Post by gordon18 on 2016-01-27
Why reinstall windows?? Because I just want to download and install programs without all the nonsense of opening command windows and typing in s/d..>l? k/ etc etc which no matter how many times I try it never works. I'm sure Linux is much better but I just cba with messing around. I just want things to work the first time without spending hours on Youtube watching how to do something. BTW I restarted my computer which had a Ubuntu disk in the cd-rom and when it stopped for a breath I chose to cancel installation, then I restarted windows normally and wubi was gone and everything was back to normal. That will teach me eh, no good deed goes unpunished. Thanks for all your help tho'.

---

### Post by Geoffrey_Arndt on 2016-01-27
"That will teach me eh, no good deed goes unpunished" . . . . . well, you had a little something to do with your experience. Was it really a teachable moment?  Don't think so . . . . . as you never had a real install of Ubuntu from the get go.

---

### Post by mastablasta on 2016-01-28
> **gordon18 said:**
> Why reinstall windows?? Because I just want to download and install programs without all the nonsense of opening command windows and typing in s/d..>l? k/ etc etc which no matter how many times I try it never works.

1. remember that since you can easilly install programs in Windows so can the programs themselves perform the install without your knowledge (talking about various malware here).

2. the way to install programs in Ubuntu is to use the software center, find the program and click install. this is same as on Android or iOS. only they call it google play or apple store or whatever.

3. if program is not in software center you open it's software sources and add the program's source (PPA). it will then appear in the software center. same as in Android I believe. it will get all the updates along with other software updates.

4. if a program does not have a PPA available, there is usually a .deb file, which behaves close to windows .exe file. so more or less just double click to install.

5. if a program does not have a .deb file, chances are it is a tar.gz. archive with a binary file inside (which is like zip file in windows). you extract it, and follow the instructions. usually it would require you to allow one file to be executed (right click, properties, set to executable) then you double click the file to run it. done.

6. if and only if there is also no binary file, you need the source code and you need to make sure you have all dependencies needed then you follow the instructions. which is usually copy pasting a few commands into terminal in order to compile the code. by the way you would have to do pretty much the same in windows if only source is available.

finally, use what works best for you. I only wrote the above so you would know there is usually no need for terminal commands to be involved in installing a file on Linux desktop. 

if you are happy with windows it is better to use windows. I use it too and I like even the 8.1 version. there are many issues with Linux Desktop, many things that IMO should be improved, but installing isn't one of them! it works pretty well as it is and offers a few additional layers of security that windows does not.

---

