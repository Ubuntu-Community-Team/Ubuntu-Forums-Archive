---
title: "install questions from a newbie"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by addison3 on 2008-07-20
Hi, I'm planning on doing an ubuntu install on my comp very soon and I have just a few questions about the process I hope can be answered for me (I am planning on doing a dual-boot with linux and xp)

1. Is it possible to keep all necessary ubuntu partitions on an external drive, leaving only the boot partion on the computer's harddrive? Basically, I want to keep as much of my main hard drive's space as possible devoted to xp and keep everything I can related to linux on my external drive. What's the smallest amount of space I could have my linux boot partition take up on my main hard drive?

2. I'm considering using filesystem encryption for linux, and I understnad ubuntu now has this as an option during installation. Which installation method do I need to choose if I want to encrypt, and what options does ubuntu's default encryption have? What encryption engines are supported by default? (like Twofish, AES). Can I use cascading encryption engines? Is it best to use ubuntu's filesystem encryption options, or to use some other program for this purpose? Can ubuntu encrypt every partition I need it to? (home, swap... basically, everything except the boot partition, obviously)

3. How can I expect speed to be affected by using both encryption and having everything on an external usb 2.0 drive?

4. Can I do something like configure my bootloader program to load xp by default, and only give me the option of loading ubuntu on a specific keystroke? What options does ubuntu's bootloader have, and are there other bootloaders with more options available?

5. Is it best to begin the dual-boot installation process by reinstalling xp first, or by having ubuntu installed first on a formatted drive, or somethign else?

That's all I can think of for now, thanks so much for the help!

---

### Post by mevets on 2008-07-20
2. I can only answer part of what you asked there, but it can encrypt the root (/), home, and swap.

3. I use encryption and I have not noticed any slow down. If you are going to get a bottleneck its going to be the usb 2.0. The best way to find out just how slow its going to be would be to test it out unfortunetly, but yeah it slows things down just as you would expect.

4. GRUB will have a list of OS's with Ubuntu pre-selected. You can change this by editting GRUB's config file.

5. Install XP first, then Linux.

---

### Post by loboc on 2008-07-20
> **mevets said:**
> 2. I can only answer part of what you asked there, but it can encrypt the root (/), home, and swap.

3. I use encryption and I have not noticed any slow down. If you are going to get a bottleneck its going to be the usb 2.0. The best way to find out just how slow its going to be would be to test it out unfortunetly, but yeah it slows things down just as you would expect.

4. GRUB will have a list of OS's with Ubuntu pre-selected. You can change this by editting GRUB's config file.

5. Install XP first, then Linux.


4. GRUB will have a list of OS's with Ubuntu pre-selected. You can change this by editting GRUB's config file. BY 

reading this  and using it
[URL="http://www.gnu.org/software/grub/manual/grub.html"]
http://www.gnu.org/software/grub/manual/grub.html[/URL]

---

### Post by addison3 on 2008-07-20
Thanks mevets and loboc for the help,I might ask around on the security forum for help with some of the questions about encryption.

Mevets, did you start using encryption when you installed ubuntu, or did you set it up later? What would you suggest as the easiest way to set it up? If you selected filesystem encryption as an option when you installed ubuntu, which installation method did you use that allowed encryption (cd, internet, etc.).

If I decide I want to install ubuntu on my main hard drive instead of the usb drive for speed reasons, what's the recommended smallest amount of space I could have linux take up on my main drive and still have it run well? As I said, I want to save most of my main hard drive's space for xp.

I scanned through the GRUB manual but couldn't find what I was looking for. Is it possible to basically only have GRUB appear and allow me to select between operating systems when I press a specific keystroke on startup? Basically, I want my computer to automatically load into xp when unattended on startup without an OS selection screen appearing.

Thanks again for the help!

---

### Post by Sef on 2008-07-20
> Basically, I want my computer to automatically load into xp when unattended on startup without an OS selection screen appearing.

Ubuntu will be the [default OS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS"), but you can change it to XP.

---

### Post by mevets on 2008-07-20
I setup encryption via the alternate install CD, so I did it at installation. There are ways to encrypt just your home folder if its on another parition ([https://help.ubuntu.com/community/EncryptedFilesystemHowto3](https://help.ubuntu.com/community/EncryptedFilesystemHowto3)). When I had trouble installing a dual-boot w/ crypto I posted a thread about it and someone responded with a really good tutorial ([http://ubuntuforums.org/showthread.php?t=847936](http://ubuntuforums.org/showthread.php?t=847936)).

I believe I used AES, but I'm not sure. It was the default. It offers several encryption methods.

Minimum requirements say 4GB is needed to install Ubuntu, but 8 is recommended.

When GRUB launches it will countdown from 10 if you dont touch anything. When 10 seconds have elapsed it will boot the default, which is Ubuntu. You can change the default to XP by going into /boot/grub/menu.lst and looking for
```

default 0

```
0 is the first item in the list, 1 is the second item in the list, and so on. XP will be 4 if I remember correctly. So yeah, you can leave the computer unattended it will boot XP automatically.

---

### Post by addison3 on 2008-07-20
thanks mevets, I think that about covers everything. That thread you linked to looks really helpful, I'll be sure to read through it.

---

### Post by addison3 on 2008-07-20
One more question, mevets. I notice in the thread you posted a link to, the person who helped you recommended skipping making the encrypted swap partition because of a bug, and recommeneded making the encrypted swap partition manually later. How would I do that once I have everything else set up? I want to make sure my swap partition is encrypted as everything else is.

---

### Post by mevets on 2008-07-20
I didnt take any steps to encrypt my swap so I couldn't tell you but the simplest guide I could find was this: [http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu](http://blog.gnist.org/article.php?story=EncryptedSwapAndHomeUbuntu)

---

### Post by The Cog on 2008-07-20
I believe that if you install Ubuntu on an external drive, then the machine becomes completely unbootabel unless that drive is connected. You will not be able to boot Windows without the external drive being plugged in because the GRUB bootloader relies on files that go on the Linux filesystem.

You should at least locate a /boot partition on the internal drive to prevent the above problem. The files the GRUB bootloader needs go in the /boot partition. This partition need only be a few hundred meg (mine is currently at 71M used).

Actually, I think using whole-disk encryption requires establishing an unencrypted /boot partition anyway.

---

### Post by addison3 on 2008-07-20
Thanks Cog. Having my comp unbootable without my external drive plugged in is definitely something I want to avoid. I was thinking about having at least the boot partition on my internal drive anyway.

I'm still deciding whether freeing up space on my internal drive by installing my other ubuntu partitions of the external drive is worth the tradeoff in speed. I guess it depends partially on what kind of reading and writing I'll be doing. I wonder exactly how much of a speed hit I could expect from having all my partitions except /boot on a usb 2.0 drive rather than my internal drive. Has anyone ever tried this?

I notice there is a 8.04 and 8.04.1 release of the latest version of ubuntu. Does anyone know if the bug mentioned in the thread mevets posted a link to is fixed in the 8.04.1 installer? (the bug where the installer freezes when trying to set up an encrypted swap with a random key) Because making the encrypted swap during installation sounds a lot easier than having to go back later and make it encrypted.

What are the differences between 8.04 and 8.04.1?

---

### Post by ugm6hr on 2008-07-20
8.04.1 is merely 8.04 with all the updates to date (well, untill about 2 weeks ago) - think of it like a Service Pack release.

A potential solution if you decide to put Ubuntu on an external HD is to install the Ubuntu bootloader (grub) on the USB (i.e. have nothing on the internal HD), and set your computer to boot from USB first.

This would mean Ubuntu would boot as default if it is plugged in, but boot Windows if it is not.

---

### Post by addison3 on 2008-07-20
> **ugm6hr said:**
> 8.04.1 is merely 8.04 with all the updates to date (well, untill about 2 weeks ago) - think of it like a Service Pack release.

Do you know if the bug during install mentioned by hyper_ch at [http://ubuntuforums.org/showthread.php?t=847936](http://ubuntuforums.org/showthread.php?t=847936) is fixed in 8.04.1?

> A potential solution if you decide to put Ubuntu on an external HD is to install the Ubuntu bootloader (grub) on the USB (i.e. have nothing on the internal HD), and set your computer to boot from USB first.

This would mean Ubuntu would boot as default if it is plugged in, but boot Windows if it is not.

Cool, is this somethign I could setup through the menus during the ubuntu install, or would it take a lot of manual adjustment later? Because as an ubuntu newb, I'm a little afraid of having to do a lot of command line type editing.

---

### Post by addison3 on 2008-07-20
^bump

---

### Post by mevets on 2008-07-20
The bug report does not say its fixed, so I'd assume it is not fixed. Additionally, Im testing it out under virtualbox and its hanging at 47% as others reported in the bug report.

---

### Post by addison3 on 2008-07-20
> **mevets said:**
> The bug report does not say its fixed, so I'd assume it is not fixed. Additionally, Im testing it out under virtualbox and its hanging at 47% as others reported in the bug report.

Thanks for all the help. It looks like I can look forward to doing command line stuff and having to encrypt the swap manually. Not something I'm looking forward to being a complete newbie to all this, but maybe it'll help me understand everything better.

---

### Post by ugm6hr on 2008-07-20
> **addison3 said:**
> Cool, is this somethign I could setup through the menus during the ubuntu install, or would it take a lot of manual adjustment later? Because as an ubuntu newb, I'm a little afraid of having to do a lot of command line type editing.

This should work without any extra work.  There are plenty of How-Tos on installing to a USB drive - try searching on pendrivelinux.com

---

