---
title: "If grub goes nuts can I use a usb flash drive as a failsafe bootloader?"
date: 2021-02-01
forum: New to Ubuntu
---

### Post by david503 on 2021-02-01
I'm actually not "new to Ubuntu", I've been using it for 5 years and I'm a LAMP developer for 20 lol.  

But in seriousness this is still my main fear while running ubuntu as my desktop workstation OS (as I currently still do) and I bet a lot of newcomers feel the same way, so this seems the right forum to post, so here it is:

My worst nightmare is getting a grub prompt.

Where you reboot and it just says:

```

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>

```

oh god kill me. 

In other words, one day you  just innocently restart and out of nowhere you get that in your face. In the past when it happened my blood runs cold and I switch to my laptop and go on forums  and eventually I just give up and entirely reinstall ubuntu.  (Which, as an advanced developer (20+ years), that's like 4 days of work with all of what I use, counting the data recovery.)

The "Boot Repair" GUI utility from a live disc has *never* worked in any of those disasters. It never fixes anything. 

I fear the grub prompt so much that when I need to reboot into windows to do something (it's a seperate drive), that the virtualbox windows isn't sufficient for,  I actually open my pc and unplug the linux drive so that windows doesn't mess with the boot block of the linux drive (which windows sometimes does... which leads to a grub prompt) before I boot into windows.  

So my question is- is there, like a usb flash disk I can make, where even if windows messes with the linux drive (or, hell, the linux drive messes with itself because of an upgrade), I can always just boot into the usb drive and it'll I just click on a list of drives and pick the linux drive or whatever. 

I'm not just talking about just a live disc/flash (well or ok- how do I do that within a live disc?), I mean specifically how could I just bypass the grub prompt disaster and instead just boot into a flash stick and point the computer at the hard drive to boot to that. "Here, computer, this is the linux drive, it's got ubuntu on it, boot to it. Don't give me a grub prompt, just go into ubuntu." 

Why is this difficult?

I'm reaaaally trying to avoid learning low-level grub stuff. I don't want to have to learn what to type at that prompt.  Call that irrational if you want, but that's a skill I don't think I should need to have.  Like learning assembly language or something.  There's even that lower level where you have to type specific sectors of the drive?? Kill me, I choose death. I don't know why that's so hard; it's like- Look-  mac users don't need to know that stuff, windows users don't need to know that, why do we?

thanks

---

### Post by oldfred on 2021-02-01
I have multiple larger flash drives, some full installs & others just grub2 and configured to boot various repair ISOs on flash drive using grub2's loopmount.
I also found an old 256MB flash drive & rEFInd fit nicely on that old flash drive.

At minimum I have current version of full version of Ubuntu, probably a couple of older versions, current gparted, instructions on how to add Boot-Repair (often more to see report which may show issue). Boot-Repair does not fix many issues, it mostly reinstalls grub or updates grub menu.
I often also have SuperGrub which can boot an otherwise bootable system. 
Most of my installs are now from one drive to another loopmounting ISO, so do not have a live installer, probably should.

---

### Post by grahammechanical on 2021-02-01
It has been a very long time since I last saw a grub prompt even on the Ubuntu development version which I have been dual booting into for more years then you have be using Ubuntu. I think that you are overstating the threat. A lot of people have problems loading Ubuntu when Windows updates and either switches fast boot back on or overwrites the efi boot partition. I suggest that Windows causes more Ubuntu boot problems than Grub suddenly deciding to take a vacation.

The Ubuntu live session does give us an option to boot from the first hard disk, whatever OS is on the drive. We press any key when we are at the purple screen with the icon of a keyboard & a human at the bottom of the screen. I suspect that this action will attempt to load Grub which will not get very far if there is something wrong with the Grub configuration files or the Linux kernel. Such as being missing.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Loading to a Grub rescue prompt must surely come after the Grub menu appears and we allow Grub to attempt to load a Linux kernel. At the Grub menu we can select Advanced Options for Ubuntu. Under those advanced options we can choose to load to a different Linux kernel. There should always be at least two kernels present. We can also choose to load a kernel with a recovery mode option. If that loads we get the following options:

resume - Resume normal boot
clean - Try to make free space
dpkg - Repair broken packages
failsafeX - Run in failsafe graphic mode
fsck - Check all files systems
grub - Update Grub boot loader
network - Enable networking
root - drop to a root shell prompt
system-summary - System summary

This is, of course, assuming that selecting a Linux kernel with Recovery mode does not dump you at the Grub rescue prompt. Everything happens for a reason. Identifying that reason is not easy. Running Boot Repair from a Ubuntu live session will allow us to produce a summary report which will be stored at Pastebin and we can put a link to the report in a question on this forum where others can examine the report and advise on what the problem is and what might be the solution. And Boot Repair will re-install Grub for us. Even if it does re-install it on every drive.

We have options because there are options and the user of any computer or device that is a computer by another name who is worried by what may go wrong should take precautions for the day when the buttered slice of bread is dropped and lands butter side down.

Regards

---

### Post by oldfred on 2021-02-01
I plugged in my SSD that is now in a USB adapter.
It changed things around & I got the grub> command.
But I was able to manually boot with 
grub> configfile (hdX,gptY)/boot/grub/grub.cfg
And I had to use ls to search for which drive was hdX and then the partition on that drive.

My USB drive renumbered my drives so hd0, become hd1. But then I also added a flash drive so boot drive then was hd2. 
And for whatever reason my UEFI got confused, it should have used GUID/partUUID and then grub use UUID.

My other system is an older Asus. And if I have all my drives plugged in each with bootable ESP, it gets so confused,sometimes I can only boot with rEFInd after removing most or all my other drives. It does not like me having lots of UEFI boot entries.

---

### Post by C.S.Cameron on 2021-02-01
I have a Full install USB that boots both BIOS and UEFI.
I plugged it into my dual boot computer and ran sudo update-grub
I saved the menuentries and did the same for other computers in the house.
I also added menuentries to boot an Ubuntu ISO file and a Live USB stick.
Then added all the menuentries to /etc/grub.d/40_custom and ran sudo update-grub again.
Now I can use the USB to boot both Windows or Ubuntu from all my internal and external drives.

---

### Post by tea for one on 2021-02-02
This looks like an interesting boot repair idea.
When you run 
> **C.S.Cameron said:**
> I plugged it into my dual boot computer and ran sudo update-grub
Are you using the OS on your Full Install USB or the OS on your dual boot computer?

---

### Post by C.S.Cameron on 2021-02-02
I boot the Full install USB drive to update GRUB on it with the computer's OS's menuentries.
I save the menuentries to /etc/grub.d/40_custom.
If there are both BIOS only and UEFI only OS on the computer, I need to run update-grub, booting once in BIOS and again booting in UEFI mode.
I can use the Full install USB to boot all the OS's on all the computers and various external drives.

On one computer I had only Windows and did not want to mess with it's bootloader. I used GParted to copy/paste the Ubuntu root partition to it from another drive. I use the USB when I want to run Ubuntu from that computer.

---

### Post by david503 on 2021-02-02
> **grahammechanical said:**
> It has been a very long time since I last saw a grub prompt even on the Ubuntu development version which I have been dual booting into for more years then you have be using Ubuntu. I think that you are overstating the threat. A lot of people have problems loading Ubuntu when Windows updates and either switches fast boot back on or overwrites the efi boot partition. I suggest that Windows causes more Ubuntu boot problems than Grub suddenly deciding to take a vacation.



Yes, exactly as I said, so hence I get under my desk and open the case to boot into windows, as I said, that's the situation I want to never have to do anymore. 

[QUOTE=grahammechanical]
Loading to a Grub rescue prompt must surely come after the Grub menu appears and we allow Grub to attempt to load a Linux kernel. At the Grub menu we can select Advanced Options for Ubuntu. Under those advanced options we can choose to load to a different Linux kernel. There should always be at least two kernels present. We can also choose to load a kernel with a recovery mode option. If that loads we get the following options:

resume - Resume normal boot
clean - Try to make free space
dpkg - Repair broken packages
failsafeX - Run in failsafe graphic mode
fsck - Check all files systems
grub - Update Grub boot loader
network - Enable networking
root - drop to a root shell prompt
system-summary - System summary

This is, of course, assuming that selecting a Linux kernel with Recovery mode does not dump you at the Grub rescue prompt. Everything happens for a reason. Identifying that reason is not easy. Running Boot Repair from a Ubuntu live session will allow us to produce a summary report which will be stored at Pastebin and we can put a link to the report in a question on this forum where others can examine the report and advise on what the problem is and what might be the solution. And Boot Repair will re-install Grub for us. Even if it does re-install it on every drive.

We have options because there are options and the user of any computer or device that is a computer by another name who is worried by what may go wrong should take precautions for the day when the buttered slice of bread is dropped and lands butter side down.

Regards[/QUOTE]

See, all of the above is what I'm trying to avoid having to deal with.  Why do we have to know this stuff to avoid a crippled workstation but the windows and mac people don't? Why isn't this simple?

---

### Post by david503 on 2021-02-02
> **C.S.Cameron said:**
> I have a Full install USB that boots both BIOS and UEFI.
I plugged it into my dual boot computer and ran sudo update-grub
I saved the menuentries and did the same for other computers in the house.
I also added menuentries to boot an Ubuntu ISO file and a Live USB stick.
Then added all the menuentries to /etc/grub.d/40_custom and ran sudo update-grub again.
Now I can use the USB to boot both Windows or Ubuntu from all my internal and external drives.

OK this sounds good, but don't you end up with the same problem- if you choose the ubuntu drive,  you end up with the grub prompt when that drive tries to boot right?

---

### Post by david503 on 2021-02-02
> **oldfred said:**
> I plugged in my SSD that is now in a USB adapter.
It changed things around & I got the grub> command.
But I was able to manually boot with 
grub> configfile (hdX,gptY)/boot/grub/grub.cfg
And I had to use ls to search for which drive was hdX and then the partition on that drive.

My USB drive renumbered my drives so hd0, become hd1. But then I also added a flash drive so boot drive then was hd2. 
And for whatever reason my UEFI got confused, it should have used GUID/partUUID and then grub use UUID.

My other system is an older Asus. And if I have all my drives plugged in each with bootable ESP, it gets so confused,sometimes I can only boot with rEFInd after removing most or all my other drives. It does not like me having lots of UEFI boot entries.

Right this brings up another fear- if I add or remove a hard drive is grub going to freak out and choke and get confused?  

Once again I wish there was just a "here, this is the drive/partition I want, boot from this drive" solution, I don't understand the complexity of the problem here.

---

### Post by poorguy on 2021-02-02
> **david503 said:**
> 
oh god kill me. 
 
Pretty radical there dude.

Reminds me of the burnt out ***Software Engineers*** I use to work around at*** General Electric / Honeywell ***who sat in little rooms by themselves all day writing ***Machine Language.***

---

### Post by tea for one on 2021-02-02
> **C.S.Cameron said:**
> I boot the Full install USB drive to update GRUB on it with the computer's OS's menuentries.
I save the menuentries to /etc/grub.d/40_custom.
If there are both BIOS only and UEFI only OS on the computer, I need to run update-grub, booting once in BIOS and again booting in UEFI mode.
I can use the Full install USB to boot all the OS's on all the computers and various external drives.

On one computer I had only Windows and did not want to mess with it's bootloader. I used GParted to copy/paste the Ubuntu root partition to it from another drive. I use the USB when I want to run Ubuntu from that computer.

Thank you [COLOR="#0000FF"]C.S.Cameron[/COLOR], your idea is very inventive - a personal boot repair device.

Of course, once you have used your [COLOR="#0000FF"]Full Install USB[/COLOR] to access a non-booting PC, then, at least, you have internet available to search how to repair, configure, reinstall grub2.

A clever alternative approach.

---

### Post by grahammechanical on 2021-02-02
> Why do we have to know this stuff to avoid a crippled workstation but the windows and mac people don't? Why isn't this simple?

The Windows and Mac people do not dual boot with an OS that they are in competition with and are trying to prevent people from using. This situation is complex because to use Linux we need to dual boot with Windows. I do not know if it is possible to dual boot with a Mac. The owners of both Microsoft and Apple have spent years locking users into their own products and have cared little about making it easy for commercial rivals to do business with users of their respective operating systems.

If the desire is to have a quite life untroubled by boot problems, then buy a machine with Linux pre-installed. If the version of Linux is Ubuntu, then make sure that the version of Ubuntu is an LTS (Long Term Support) and then do not make too many changes to the desktop environment. Keep the user interface default. Then when the time to upgrade to the next supported LTS version comes along there will be a strong likelihood that the upgrade process will be successful.

An alternative to the above suggestion is to build your own machine. I have done that. There are also complexities in going that route. Is the hardware compatible with Linux? A lot of hardware manufacturers are unwilling to cooperate with Linux developers to make Linux compatible with their hardware. They want to keep in favour with the very big corporations that are providing them with operating systems.

And as you have no doubt found out a lot of application developers are not interested in providing Linux versions of their applications. Or, in keep them feature for feature compatible with the windows versions. So, you are back to dual booting again.

Regards

---

### Post by david503 on 2021-02-03
> **grahammechanical said:**
> The Windows and Mac people do not dual boot with an OS that they are in competition with and are trying to prevent people from using. This situation is complex because to use Linux we need to dual boot with Windows. I do not know if it is possible to dual boot with a Mac. The owners of both Microsoft and Apple have spent years locking users into their own products and have cared little about making it easy for commercial rivals to do business with users of their respective operating systems.
Regards


You can dual boot to windows on a mac.  In fact apple has had that built into it's os since 2005.

[https://en.wikipedia.org/wiki/Boot_Camp_(software)](https://en.wikipedia.org/wiki/Boot_Camp_(software))

---

