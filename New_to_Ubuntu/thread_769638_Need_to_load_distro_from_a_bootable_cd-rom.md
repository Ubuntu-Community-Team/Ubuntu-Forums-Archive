---
title: "Need to load distro from a bootable cd-rom"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by websquad on 2008-04-26
I have a new computer with a freshly-wiped hard drive. No installed OS, so it will not boot.

Which Ubuntu distro do use for a clean install that can be booted from a cd-rom, and how do I make the cd-rom (or dvd-rom) bootable.

For what it is worth, I know nothing about Linux in general and Ubunto in specific; insider buzz words are incomprehensible to me.

Is this something I can do, or do I need to load XP to get a Ubunto installation going.

Thanks ....

---

### Post by NeoLithium on 2008-04-26
Just head here [http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu) And grab yourself a copy of Ubuntu that you need, be it 32 or 64 bit; burn it to disc, fire it in the tray and reboot :)  If it doesn't end up booting from the CD, you may need to enter your BIOS and check your boot order, and make sure that your CD drive is tried before hard disks.  The process varies from BIOS to BIOS, but is generally quite easy to find where you need to look; should that issue come up.

The desktop CD's boot into a live environment, letting you basically be inside ubuntu though it's running from your CD drive, not your hard drive.  Server doesn't give you a nice GUI, it's a text installer, so you may want to go for the desktop version.

---

### Post by celticbhoy on 2008-04-26
Download ISO image from here

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

And then simply burn to a blank disk using appropriate software

---

### Post by frup on 2008-04-26
> **websquad said:**
> I have a new computer with a freshly-wiped hard drive. No installed OS, so it will not boot.

Which Ubuntu distro do use for a clean install that can be booted from a cd-rom, and how do I make the cd-rom (or dvd-rom) bootable.

For what it is worth, I know nothing about Linux in general and Ubunto in specific; insider buzz words are incomprehensible to me.

Is this something I can do, or do I need to load XP to get a Ubunto installation going.

Thanks ....

Do you already have a CD/DVD? If you don't and can download one you need to burn the iso correctly so that it is bootable. If you find this hard ask for more specific instructions or request a CD from shipit. This will take 6 weeks to arrive though.

From here (and if you have a CD/DVD) you need to make sure booting from CD/DVD is enabled in your bios. When you turn on your computer at the beginning the bios can be accessed in the first few seconds as the memory is loaded and the drives etc are found. All the computers I have use the delete key to access the bios although I know other keys are used too. 

In the bios you change the order of which drive to boot from. Place CD first and then HDD second for example. Key words here are things like peripherals. A bios shouldn't be hard to work out though. Save and quit

Place the CD/DVD in the tray and it should load. You go through the Ubuntu installation process and at the end of it you should have a working computer.

---

### Post by websquad on 2008-04-26
(1) My new Windows/XP-based system has a CD-ROM/DVD burner and I have broadband to the web, so I'm prepared for the download.

(2) The first response gave me a URL which pointed me to this web page:

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/)

Version 8.04 ("Hardy Heron" ... where do they come up with those names?) appears to be what I want (please correct me if I'm wrong). So do I just download it and copy it to a CD-ROM?  That will not make it bootable, will it?

---

### Post by marine63 on 2008-04-26
you need to use a burning program
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
after your done using this tutorial just pop the cd in the cd driver and restart your computer go to bios configure bios to make computer boot cd before harddrive does and save and then the cd will boot when you come to the ubuntu menu screen go to check for errors and then if you have no problems install it

you do have a blank cd too right?

---

### Post by NeoLithium on 2008-04-26
> **websquad said:**
> (1) My new Windows/XP-based system has a CD-ROM/DVD burner and I have broadband to the web, so I'm prepared for the download.

(2) The first response gave me a URL which pointed me to this web page:

[http://www.gtlib.gatech.edu/pub/ubuntu-releases/](http://www.gtlib.gatech.edu/pub/ubuntu-releases/)

Version 8.04 ("Hardy Heron" ... where do they come up with those names?) appears to be what I want (please correct me if I'm wrong). So do I just download it and copy it to a CD-ROM?  That will not make it bootable, will it?

Best thing to do, is with your burning software is to ensure you burn it as a disk image, which will make it bootable.  Other ways will tend to give you a copy of the .iso image on the disc making it an annoying frisbee. There's some information on making sure you're burning right, at this link:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Hope this helps :)

---

### Post by websquad on 2008-04-26
How did you guys get so smart!!

Thanks.  You are opening up a whole new world for me.

Today I found 22 inch wide-screen LCD display at Circuit City for $140US.  New (to me) display, new (to me) computer. New opportunities.  Freedom from Windows software?  One can hope!

Thanks again!  The disk just ejected.  I'm off to the races!

---

### Post by websquad on 2008-04-26
The installation is, I assume, concluded.  I have a window which says something like "Installation is complete.  We need to restart the computer to use the new installation.  You can continue to use the live CD, although any changes you make or documents you save will not be preserved."  

Gives two options:
  [Continue using the live CD]
  [Restart now]

I tried to eject the CD and nothing happened.  I tried to click the [Restart now] button and the CD started spinning, but nothing I could observe happened.

I'm sorta stuck.  Don't want to screw up.  Any ideas?

---

### Post by Zralou on 2008-04-26
It won't let you eject the CD while running on the 'liveCD', but hitting 'reboot now' should just restart the system (half way through shutting down, it will spit out the CD and ask you to remove the media and hit enter).

Sara Lou

---

### Post by websquad on 2008-04-27
Clicking [Restart now] resulted in nothing happening.

So I powered down. Then powered up. Immediately pushed the eject lever and got the CD-ROM drive.

It prompted me for a userid and password.  I thought I remembered it, but apparently not.  What are my options now?

---

