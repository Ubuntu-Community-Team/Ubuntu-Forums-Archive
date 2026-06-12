---
title: "[SOLVED] Where can I download a live CD for HP architecture?"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by gshockxc on 2008-11-30
I've got a friend who has an HP ze4540 laptop, and I downloaded the appropriate Ubuntu Hardy image file for HP-PA/RISC.  But I wanted to run the live CD to give the owner the opportunity to see Ubuntu in action before installing.  When I run the install CD, it doesn't give me the option to run Live CD like it does on other platforms. 

Can anyone point me in the right direction?

Thanks, 
-gshockxc

---

### Post by oilchangeguy on 2008-11-30
> **gshockxc said:**
> I've got a friend who has an HP ze4540 laptop, and I downloaded the appropriate Ubuntu Hardy image file for HP-PA/RISC.  But I wanted to run the live CD to give the owner the opportunity to see Ubuntu in action before installing.  When I run the install CD, it doesn't give me the option to run Live CD like it does on other platforms. 

Can anyone point me in the right direction?

Thanks, 
-gshockxc

the hp does not require some special cd. are you sure you correctly burned the live cd? and this computer is set to boot from the cd drive first.

---

### Post by gshockxc on 2008-11-30
> **oilchangeguy said:**
> the hp does not require some special cd. are you sure you correctly burned the live cd? and this computer is set to boot from the cd drive first.

Welcome to my world.

Here's the link in the documentation where I found, what I thought was, the method for installing the right platform of Ubuntu.
[https://help.ubuntu.com/8.04/installation-guide/index.html](https://help.ubuntu.com/8.04/installation-guide/index.html)

I guess I misunderstood.  Is this for older versions of HP systems?

I tried Hardy this summer on the same laptop and it wouldn't install.  I can't guarantee that there wasn't an error on the CD at the time.  It's running an Intel processor, and it's a 2003 laptop, so 32-bit should work, right?

Maybe I goofed on the other install and that's why I thought I needed this alternate.  

Thanks, 
-gshockxc

---

### Post by oilchangeguy on 2008-11-30
> **gshockxc said:**
> Welcome to my world.

Here's the link in the documentation where I found, what I thought was, the method for installing the right platform of Ubuntu.
[https://help.ubuntu.com/8.04/installation-guide/index.html](https://help.ubuntu.com/8.04/installation-guide/index.html)

I guess I misunderstood.  Is this for older versions of HP systems?

I tried Hardy this summer on the same laptop and it wouldn't install.  I can't guarantee that there wasn't an error on the CD at the time.  It's running an Intel processor, and it's a 2003 laptop, so 32-bit should work, right?

Maybe I goofed on the other install and that's why I thought I needed this alternate.  

Thanks, 
-gshockxc

the alternate cd is NOT a live cd. it's a texted based installer. what are the specs of this computer?

---

### Post by gshockxc on 2008-11-30
> **oilchangeguy said:**
> the alternate cd is NOT a live cd. it's a texted based installer. what are the specs of this computer?

Here are the specs:
[LIST]
[*]Microprocessor   	Mobile Intel Celeron Processor - 2.4 GHz
[*]Microprocessor Cache 	256KB (L2)
[*]Memory 	256MB DDR SDRAM (1 x 256MB) at 266MHz **Updgraded to 512MB**
[*]Memory Max 	1024MB DDR SDRAM (2 x 512MB)
[*]Video Graphics 	ATI MOBILITY RADEON 4X AGP and 3D architecture
[*]Video Memory 	64MB DDR SDRAM (shared)
[*]Hard Drive 	40GB enhanced-IDE hard disk drive      **Upgraded to 100GB**
[*]Diskette Drive 	None
[*]Multimedia Drive 	DVD-ROM/CD-RW Combo
[*]Display 	38 cm (15.0 inch) XGA TFT (1024 x 768) display
[*]Fax/Modem 	Integrated v.90/v.92 56KB modem (RJ-11 connector)
[*]Network Card 	Integrated 10/100BASE-T Ethernet LAN (RJ-45 connector)
[*]Wireless Connectivity 	Not included
[*]Sound 	16-bit Sound Blaster Pro-compatible audio

[*]Internal Altec Lansing speakers
[*]Keyboard 	88-key
[*]Pointing Device 	Touch Pad with On/Off button and dedicated vertical Scroll Up/Down pad
[*]PC Card Slots 	
* One Type I/II/III
* 32-bit card bus


[*]External Ports 	
    * Two Universal Serial Bus (USB) 1.1
    * Parallel (25-pin)
    * One Serial
    * One PS/2 keyboard/mouse
    * One headphone-out
    * One microphone-in
    * One VGA (15-pin)
    * One TV-Out (S-video)
    * One RJ-11 (modem)
    * One RJ -45 (LAN)
    * One PCI (port replicator)
[/LIST]

---

### Post by linuxguymarshall on 2008-11-30
I have an HP and I will admit that installing linux on it is a pain in the *** however the Live CD should have the right options. Did you check your MD5 sum of the ISO?

---

### Post by gshockxc on 2008-11-30
> **linuxguymarshall said:**
> I have an HP and I will admit that installing linux on it is a pain in the *** however the Live CD should have the right options. Did you check your MD5 sum of the ISO?

I have to admit, I did not check the MD5sum.  It was a CD that I burned  probably a year before trying it on the HP.  I'm downloading the newest version of Hardy, and will try the Live CD again.  I will run the MD5sum before trying this time.

Thanks,

---

### Post by gshockxc on 2008-11-30
I checked the MD5sum, and it's correct.  So I put the Hardy CD in, and booted from it.  It loaded Ubuntu, and brought up a portion of the Hardy wallpaper.  There are still no menus, and the upper left quadrant of the screen is a white rectangle.  The hard drive light shows no activity, and the CD is cranking away as though it's doing something. But there is no progress.  

I'm only running the Live CD, but this is the same response I got last time I tried to install Ubuntu on this laptop.  There's got to be a glitch somewhere.  

I just don't know where to look.

Thanks.

---

### Post by oilchangeguy on 2008-11-30
> **gshockxc said:**
> I checked the MD5sum, and it's correct.  So I put the Hardy CD in, and booted from it.  It loaded Ubuntu, and brought up a portion of the Hardy wallpaper.  There are still no menus, and the upper left quadrant of the screen is a white rectangle.  The hard drive light shows no activity, and the CD is cranking away as though it's doing something. But there is no progress.  

I'm only running the Live CD, but this is the same response I got last time I tried to install Ubuntu on this laptop.  There's got to be a glitch somewhere.  

I just don't know where to look.

Thanks.

does this computer presently have an operating system on it? is there a reason why you have to have linux (ubuntu)? try another distro, i suggest mandriva 2009 one [www.mandriva.com](www.mandriva.com). and for whatever reason some computers will not run another operating system. The computer i'm using now is a custom built rig, it has more than enough power to run linux. i've tried several distro's live cd's to no avail. most will not load the desk top. so it will stay with xp pro (legal copy), which runs fine.

---

### Post by gshockxc on 2008-11-30
> **oilchangeguy said:**
> does this computer presently have an operating system on it? is there a reason why you have to have linux (ubuntu)? try another distro, i suggest mandriva 2009 one [www.mandriva.com](www.mandriva.com). and for whatever reason some computers will not run another operating system. The computer i'm using now is a custom built rig, it has more than enough power to run linux. i've tried several distro's live cd's to no avail. most will not load the desk top. so it will stay with xp pro (legal copy), which runs fine.

It does currently have XP on it.  I suspect that it's just like you have said.  No, there's no reason that this machine HAS to be a linux 'top.  I just wanted to show my friend because I thought they would like it better than XP.  But it's just basic word processing so it's no big deal.  And I've got OOov3 on it, so it will get the job done more than adequately.

Thanks.

---

### Post by SunnyRabbiera on 2008-11-30
I sense the ATI card is at fault here, ATI support in linux in general is p!$$ poor at best but that is more ATI then us.
Everything else should work under linux, but maybe an alternate distro is a good idea.
Mandriva is a good suggestion, as is Mepis and Linux Mint.

---

