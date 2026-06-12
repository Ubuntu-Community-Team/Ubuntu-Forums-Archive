---
title: "Keeping GRUB, Ubuntu, and Vista Separate"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by GreyArea2 on 2008-07-09
Hello all, 

I'm a long-time computer user looking to get into Linux, specifically Ubuntu, for the first time. However, there's a very specific way I want it to work, and Ubuntu doesn't seem willing to cooperate. I'm quite picky about what goes on in my computer, and I need your help to get a set up that complies with my unique concerns. My whole problem comes down to the GRUB boot-loader; I don't want it on my Vista hard drive, or anywhere related to Vista at all. 

Here's my set up: I have three hard drives, one for Windows Vista, one empty (awaiting Ubuntu if you can help me get it working), and one for storage. I want those separated. The Vista drive is my first boot device, the empty/Ubuntu is second, with storage third.

This is what I want to happen: When I just turn my PC on, like normal, it should boot to Windows Vista, with no delay whatsoever, and especially, no boot menu _period_. If I just hit the power button, I want to see a perfectly normal Windows Vista boot; I want it to act as though the Ubuntu OS does not exist at all. Hitting F8 on boot brings up my boot menu, with my 3 hard drives and DVD drive; from there, I want to be able to select the second drive, and from there, go into Ubuntu. (Naturally, selecting the first hard drive from the F8 boot menu should boot me cleanly into Windows.) 

To this end, Ubuntu seems content to metaphorically spit in my face - I give it an entire disk of its own, but it still insists that even booting from Windows Vista's disk should show me the GRUB boot-loader, with the further audacity to put Ubuntu as the default option. If I boot from the Ubuntu disk, then and _only_ then do I want to see a boot menu, or any sign at all that there is, in fact, a Ubuntu install present. 

I don't see why it should be otherwise. Vista on one disk, Ubuntu on the other. Whatever disk I pick, that's the OS that boots. Nothing else makes a bit of sense to me. That way, if I ever decide to switch to Ubuntu fully, I can just change the boot order in the BIOS so the Ubuntu disk boots first. 

Summary: I want no boot menu (no GRUB) until I manually select the Ubuntu disk from the built-in boot menu. Otherwise, I want a clean boot, with no additional menus or prompts however brief, right into Windows. GRUB should be totally isolated on the secondary drive.

Thank you for your time, and thanks in advance for any help you are able to grant a fresh Ubuntu user. I'm really looking forward to working with this fine community.

---

### Post by ramjet_1953 on 2008-07-09
If you want to keep everything seperate, why no do what I do?

Just have seperate hard drives.

If using a desktop machine, you can get a caddy system that uses a spare 5.25" bay so that you can easily plug in and out a hard drive.

If using a laptop, most have a trapdoor in the base allowing you to change out a hard drive in a couple of minutes (this is what I do).

As far as I know, if you want to dual-boot, you must use GRUB, or LILO.

Regards,
Roger :cool:

---

### Post by bumanie on 2008-07-09
Yep, use separate hard drives. Unplug vista drive when installing ubuntu and choose which drive to boot via bios.

---

### Post by tjwoosta on 2008-07-09
GRUB is a bootloader

it does not touch your vista partiton

it installs to the MBR (Master Boot Record) of your harddrive, wich basically means its at the very beginning before any of the partititions

---

### Post by cdtech on 2008-07-09
I use a USB stick to boot my OS's if needed. Without the stick inserted my laptop boots to my Primary drive (Vista), with it inserted I can choose from Ubuntu, Vista or XP.

That's just the way I wanted it. I didn't want any conflicts with other operating systems.

---

### Post by Chelidon on 2008-07-09
Now, I'm pretty new to this, but you probably need to use one bootloader or the other, that is, either GRUB or Windows boot loader. Now, I do know of a system that allows a computer to boot into one OS or the other with a flick of a switch, but that it seems to involve Linux (in this case, a specialized flavor of Fedora) booting from a LAN. The other OS is MacOSX. Unfortunately I can't get any more specific than that. If anyone has come across such a system please let me know!

---

### Post by kansasnoob on 2008-07-09
Another option is described on Page 4  "Choose a bootloader" in this tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

But Bumanie's option in reply #3 would be my personal preference.

EDIT: I should actually say that GRUB is MY preferred boot-loader!

---

### Post by BGFG on 2008-07-10
Hey i was in the exact same situation as you, i had a machine with vista preloaded, and two extra hard drives. one i use as a media dump and the other i wanted to try ubuntu on. The simple answer is a program called EasyBCD. It's especially useful if your intention is to dualboot with windows already installed.
It allowed be to install grub to the native Ubuntu harddrive then simply add ubuntu to the vista bootloader. I'm not a super advanced user so things such as choice of bootloader don't affect me as much.
Anyways, it's uber simple to use and very powerful. Plus vista's loader isn't all that bad (as far as i can tell) This way, windows can't really see my ubuntu. and ubuntu can see and read my ntfs drives and partitions. Just the way it should be.

---

### Post by GreyArea2 on 2008-07-10
> **BGFG said:**
> Hey i was in the exact same situation as you, i had a machine with vista preloaded, and two extra hard drives. one i use as a media dump and the other i wanted to try ubuntu on. The simple answer is a program called EasyBCD. It's especially useful if your intention is to dualboot with windows already installed.
It allowed be to install grub to the native Ubuntu harddrive then simply add ubuntu to the vista bootloader. I'm not a super advanced user so things such as choice of bootloader don't affect me as much.
Anyways, it's uber simple to use and very powerful. Plus vista's loader isn't all that bad (as far as i can tell) This way, windows can't really see my ubuntu. and ubuntu can see and read my ntfs drives and partitions. Just the way it should be.

Ideally, I don't want to add Ubuntu to the Vista bootloader. I want Vista's bootloader to have only Vista, and Ubuntu's bootloader (GRUB) to have only Ubuntu. Separate hard drives, separate OSes. Neither should contain any sign that the other exists. If I want to see GRUB, I'll boot the Ubuntu hard drive. I'm not even sure that can be done though - can one safely have two separate bootloaders?

Then again, you're method sounds pretty darn good - I think I'll try this.

> **tjwoosta said:**
> GRUB is a bootloader

it does not touch your vista partiton

it installs to the MBR (Master Boot Record) of your harddrive, wich basically means its at the very beginning before any of the partititions

But it touches Vista. GRUB is part of Ubuntu, by my logic. If I boot from the Vista drive, I should see no part of Ubuntu. If booting the primary drive, Vista, shows me GRUB, something is wrong. I'm pretty close to OCD in that regard - one OS here, another here, and that's that.

> **bumanie said:**
> Yep, use separate hard drives. Unplug vista drive when installing ubuntu and choose which drive to boot via bios.

Can you, or someone else provide more detail on this? Are you saying that if I unplug the Windows drive for the Ubuntu install, then plug it back in, it will be as I describe? That seems to easy... are you sure it won't just break one or both of the OSes? I'm interested if anyone has actually tried this.

Thanks for your help so far!

---

### Post by kansasnoob on 2008-07-10
> 
Quote:
Originally Posted by bumanie View Post
Yep, use separate hard drives. Unplug vista drive when installing ubuntu and choose which drive to boot via bios.
Can you, or someone else provide more detail on this? Are you saying that if I unplug the Windows drive for the Ubuntu install, then plug it back in, it will be as I describe? That seems to easy... are you sure it won't just break one or both of the OSes? I'm interested if anyone has actually tried this.



The real problem is that you'll have to boot into BIOS each time and select which hard drive to boot first if you don't have both OS's identified by one or the other boot-loader.

---

### Post by BGFG on 2008-07-10
> **kansasnoob said:**
> The real problem is that you'll have to boot into BIOS each time and select which hard drive to boot first if you don't have both OS's identified by one or the other boot-loader.

:) I think that's exactly what GreyArea2 wants....

---

### Post by rokytnji on 2008-07-10
Heres a PDF document for what you are looking for.

[www.industechnologies.com/downloads/IDEX400410_SATA_InstallGuide.pdf](www.industechnologies.com/downloads/IDEX400410_SATA_InstallGuide.pdf) -

---

### Post by bodhi.zazen on 2008-07-10
By far and away, the easiest method is to install Ubuntu with the defaults, including installing GRUB.

Grub almost always works and it is actually very easy to restore the windows boot loader if you ever want to.

You are making it harder then it really is with all the options posted in this thread.

---

### Post by tjwoosta on 2008-07-10
> By far and away, the easiest method is to install Ubuntu with the defaults, including installing GRUB.

Grub almost always works and it is actually very easy to restore the windows boot loader if you ever want to.

You are making it harder then it really is with all the options posted in this thread.

i completely second that

---

### Post by bumanie on 2008-07-10
+1 to the above, but if you stick with your original plan, what I posted earlier should work - yes it is that easy, if you don't mind changing hard drive boot order each time you want to boot a different OS. Unplugging the windows drive will mean ubuntu does not know windows is there.

---

### Post by GreyArea2 on 2008-07-10
Problem solved!

The solution was actually fairly easy. The program BGFG so kindly recommended is everything I could want and more - it single handedly solved my dual boot problem in about five minutes. 

The killer feature: it allows the user to set the time limit before it boots to the default OS (for me, Vista). Set this to 0, and my ideal situation is realized almost exactly as I described. And if I ever need to, I can just move the timer up to five or so seconds, or even set Ubuntu to the default OS. It also looks to be very open-ended, so if I ever decide to try another distro (Fedora, maybe?) I can add it in easily.

Interestingly enough, I'm actually typing this from Ubuntu. I must admit, I rather like it. 

Thanks again for all the help, and especially to BGFG for recommending EasyBCD. I'm simply amazed at the help I received in only a few hours. :-)

---

### Post by cariboo on 2008-07-10
I hate to burst your bubble, but grub does exactly want you want also, You set the default wait time to 0 and set it to boot Vista by default. The only time you see a boot menu is if you hit esc during boot up. You've just added an extra layer of complication if something does go wrong. This will of course make it harder to diagnose a problem when it does arise.

Jim

---

### Post by GreyArea2 on 2008-07-10
Yes, but doing it with EasyBCD was, well, easy. There was no need for help, no guess work, and no visible risk. Just add Ubuntu to the list, set the time to 0, and go. I by no means speak from experience, but I'm guessing using GRUB would be significantly less intuitive.

What matters is it works, and seems perfectly stable. Thanks for the advice though, all suggestions are great for future reference.

---

### Post by AFarris01 on 2008-07-10
Actually...im a little sad that i didnt find this post sooner, because this is almost exactly how my dad wanted their computer set up (sans the third storage disk)

how my dad wanted the computer set up:
windows xp hard disk #1
Ubuntu on hard disk #2
select which disk to boot from via BIOS's boot order key (f12 in our instance), essentially making BIOS the 'bootloader' and effectively isolating the 2 hard-drives from each other.  so heres how i did it:

XP was already installed on the first harddisk, so i first completely disconnected that disk.
second, i connected the 2nd (blank) hard drive, and installed Ubuntu on it.  as far as ubuntu knew, it was the only hard drive installed.

heres the tricky part:

Reconnected the XP hard drive as a 'slave' drive, with the Ubuntu disk set as 'master' (done via the on-device jumpers), then went into BIOS, and set the Windows XP disk as the first boot device, then CD/DVD drive, then floppy, then Ubuntu.

the result: 2 completely separate OS's with fully separated boot processes.
basically now, whenever they start the computer, by default a standard Windows XP boot with Windows using its own bootloader, and no extra settings/configuration/etc.  or, if he decided to boot in Ubuntu, on the BIOS screen, he can hit the F12 key, and pick the 2nd hard drive entry from the list (also listed as the last entry, or just hit "4" for quickness) which results in Ubuntu booting by itself, with nothing but Ubuntu options.

It sounds like this is exactly what the original poster was trying to do...but i'm glad it worked out all the same.  i just wanted to post this suggestion up here, just in case.

---

