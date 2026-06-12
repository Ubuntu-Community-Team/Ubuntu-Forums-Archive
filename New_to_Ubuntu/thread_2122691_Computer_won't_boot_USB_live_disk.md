---
title: "Computer won't boot USB live disk"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by scipio7 on 2013-03-05
Hello everyone! This is my first post but I've been using Ubuntu and other forms of linux for roughly 8 years now. 

Anyways, my son decided to take my computer (PC) and try to install OS X on it without my permission two days ago while I was at work. He erased my hard drive completely and installed a not-so-functional OS X on my machine. He did all this with an official OS X CD he bought (Snow Leopard).

My system prior to the OS X installation was a triple boot setup with Win7, Ubuntu 12.10, and Mint 14.

Anyways, I thought to myself "I'll just pop in the recovery Windows disk, re-install Linux, and presto! No biggie!"

I dug around for the disk and it appears that my computer didn't come with a recovery disk. It was relying on a separate recovery partition on the hdd (it was supposed to work with a "Press F3 to start recovery mode" on the POST BIOS screen), which means that I, as of now, don't have Windows anymore.

I took a USB drive, popped it into my computer, formatted it to FAT32 while making sure it was done with the MBR (instead of the Mac default GPT). I went to work yesterday, downloaded Ubuntu 12.10 on my work computer (my , home comp has no internet access), made a boot USB disk using UNetboot. Came home and the computer won't boot from the USB.

It says, 
"[COLOR=#000000][FONT=Verdana]Reboot and Select proper Boot device[/FONT][/COLOR]
[COLOR=#000000][FONT=Verdana]or Insert Boot Media in selected Boot device and press a key"

Things I have tried:
* Reverted the BIOS settings to defaults
* Setting the USB disk to first priority on the boot order
* Deleted OS X from the hdd, reformatted the hdd to MBR, FAT32
* Looking at my computer's manufacturer's website for a recovery disk or boor disk of some kind

[/FONT][/COLOR]The computer IS able to read the USB disk's "presence", along with my work computer (WindowsXP 32-Bit), which made the boot disk, along with even OS X.
It's just booting off of it that it seems it has trouble with.

As of now, my computer has no operating system. Bios is functional, so it gives me hope. I would try to do all the formatting of the USB disk on my work computer but I don't have permissions for that.

What should I do? I don't care about recovering Windows. I just want a functional PC---Windows, Linux, I don't care. Please help me! ](*,)

Thank you in advance for your help and sorry for the long post!

My system's specs:
MSI GT70-0NC
Intel i7 3610QM
Nvidia GeForce 670M
750 GB hdd

---

### Post by rohitvijaysharma on 2013-03-06
Your problem is totally recoverable so first off- don't worry. If you can get your hand on some Ubuntu machine, I suggest you try the default application "Startup Disk Creator" which is installed by default on all Ubuntu machines. UNetboot supports most distributions of linux but for some reasons, it shows problems with Ubuntu. There could be a lot of other problems but I doubt our case is as complex. Try it and I believe it should world out.

---

### Post by scipio7 on 2013-03-06
Thanks for the reply!

I did some more digging around. I tried a program called Rufus to make the boot disk. But I saw something a bit strange. It would not show my USB device. I opened the log and it says:

```
**Found drive 'ELECOM MF-MSU3 USB Device'**
[B]could not open '\\?\usbstor#disk&ven_elecom&prod_mf-msu3&rev_1.00#1270916391190086&0#{53f56307-b6bf-11d0-94f2-00a0c91efb8b}': [0x00000005] Access Denied.
0 devices found[/B]

```
So now I'm having doubts as to whether it's my work's computer that's blocking me access to write a bootable disk (again, permissions) or if my computer is just not being able to boot off it. 

Considering I won't have access to a functioning computer (without permissions) AT ALL until the weekend, I'm currently at a loss. Unless I try to reinstall OS X and try to make it do a bootable USB disk (maybe using the mac version of UNetboot..). Talk about the "hair of the dog that bit you." Bleh! :roll:

My hypothesis is that even though UNetboot is completing the process of writing the disk, it's not correctly writing the file to boot with because the system is blocking it. :-s
I would've hoped that UNetboot would warn about this, if indeed it is the case. 

I have to go to my other office right now (where I have no computer). I'll try what I mentioned above tomorrow when I come back to work and I'll post what happened! 

Thanks!

-Scipio

---

### Post by justincarter on 2013-03-06
I think you are having problem during boot. See boot loader setting and try it again.

---

### Post by scipio7 on 2013-03-07
Ok guys! Success! I have Ubuntu 12.10 64bit up and running on my computer once again! 

What I did was I reinstalled OSX. Then I placed UNetBootin and the Ubuntu iso on the USB disk. I installed UNetbootin then reformatted the disk using the Disk Utility to make it MBR, FAT32. Next, I used used UNetbootin to make the bootable USB live disk. Restarted my computer. The USB disk still would NOT boot so I went on the BIOS and changed the USB disk setting to "Forced FDD" rather than "Auto". The disk then booted flawlessly. I erased OS X, installed Ubuntu, and will be grounding my son for a month! I'm also taking away his iPad for a while.   
:-D

Anyways, I do think my work computer's permission settings were interrupting with the making of the USB disk. That said, I'm still not sure why before I had to set the settings to "Forced FDD" rather than "Automatic". It was truly trial and error. If anyone could enlighten me as to why that would be so, I'd appreciate it but as of now the problem has been solved. 

Thanks for all the replies!

Scipio

---

### Post by justincarter on 2013-03-12
Most Welcome ... You are free to ask, If you face any queries and problems.

---

