---
title: "BIOS or boot file problem?"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by Sonoran Desert Rat on 2012-09-10
Okay, I downloaded and burnt the  lubuntu iso to cd and rebooted by cd and got a message that says the  boot filename is not found. :sad:

Here is what is on the cd when I open it in windows to look at the files:

.disk
boot
casper
dists
install 
isolinux
pics
pool
preseed
autorun
md5sum
README.diskdefines
wubi

I believe the burnt cd is fine. Is it posible I'm using the wrong boot  window to boot from cd or need to do something special to boot from cd?

I checked my computer's website and I definately have it set to boot from cd!

Nutz & Boltz:

OS Name    Microsoft Windows XP Professional
Version    5.1.2600 Service Pack 3 Build 2600
OS Manufacturer    Microsoft Corporation
System Name    LAPTOP
System Manufacturer    TOSHIBA
System Model    Portable PC
System Type    X86-based PC
Processor    x86 Family 6 Model 13 Stepping 6 GenuineIntel ~1496 Mhz
BIOS Version/Date    TOSHIBA Version 1.20, 4/28/2004
SMBIOS Version    2.3
Windows Directory    C:\WINDOWS
System Directory    C:\WINDOWS\system32
Boot Device    \Device\HarddiskVolume1 :KSI SET BIOS TO BOOT FROM CD!:KS
Locale    United States
Hardware Abstraction Layer    Version = "5.1.2600.5512 (xpsp.080413-2111)"
User Name    DELETED
Time Zone    DELETED
Total Physical Memory    512.00 MB
Available Physical Memory    161.88 MB
Total Virtual Memory    2.00 GB
Available Virtual Memory    1.96 GB
Page File Space    1.13 GB
Page File    DELETED

According to the info above, am I not booting from CD?? Do I have to go somewhere else to fix this?

---

### Post by anewguy on 2012-09-10
Well, the first thing we usually ask in these cases:

- did you just burn a CD, or did you tell it burn from an image?  You must tell it to burn from an image or what you get won't boot like you want.

- is your BIOS boot order set for:

CD/DVD first
Hard disk second

If not, you should set it that way and save the changes before exiting the BIOS setup and rebooting.

Could you perhaps copy the exact message text and paste it back here?

---

### Post by Sonoran Desert Rat on 2012-09-10
> **anewguy said:**
> Well, the first thing we usually ask in these cases:

- did you just burn a CD, or did you tell it burn from an image?  You must tell it to burn from an image or what you get won't boot like you want.

- is your BIOS boot order set for:

CD/DVD first
Hard disk second

If not, you should set it that way and save the changes before exiting the BIOS setup and rebooting.

Could you perhaps copy the exact message text and paste it back here?

I used a program called "Grab and Burn" and burned from image.

My BIOS are ABSOLUTELY set to boot from CD! However (& I don't know if these make any difference?):

Device Config: Set up by OS (should this be "all devices"?)

Network Boot Protocol: PXE (should this be "RPL"?)

The exact message I get is:
No Boot Filename Recieved

...maybe I'm not actually saving the changes to BIOS? I'll check. 

and thanks :p

I am definately booting from CD!! I pulled the BIOS up and CD is first.

---

### Post by SeijiSensei on 2012-09-10
It sounds to me like the CD was not properly burned.  Do you have some other CD burning software you might try?  Do you have an existing Linux machine where you can use Brasero or K3b?  Sometimes burning at a slower speed can help, too.

You should see right away if the machine tries to boot from the CD.  Does the drive light flash?  Does it grind away after it detects the CD?  It's usually pretty obvious that the CD is being used.

---

### Post by Sonoran Desert Rat on 2012-09-10
> **SeijiSensei said:**
> It sounds to me like the CD was not properly burned.  Do you have some other CD burning software you might try?  Do you have an existing Linux machine where you can use Brasero or K3b?  Sometimes burning at a slower speed can help, too.

This will be my first linux os :guitar: I don't have access to another. :( I burned at the slowest speed possible as the ubuntu instructions directed. 

I downloaded the burner from the ImgBurn site and Grab and Burn is what I got.

And thanks!

---

### Post by steeldriver on 2012-09-10
it sounds like you maybe clicked on one of those annoying 'DOWNLOAD' buttons that is actually an ad / download for a competing product 

the real imgburn is good, or if you have Win7 the native 'Burn' from the Explorer window is good as well

on XP I would either use the real ImgBurn or there's a Microsoft command line utility called cdburn.exe that's part of the Server 2003 Resource Kit

[http://www.microsoft.com/en-us/download/details.aspx?id=17657](http://www.microsoft.com/en-us/download/details.aspx?id=17657)

---

### Post by Sonoran Desert Rat on 2012-09-10
> **steeldriver said:**
> it sounds like you maybe clicked on one of those annoying 'DOWNLOAD' buttons that is actually an ad / download for a competing product 

the real imgburn is good, or if you have Win7 the native 'Burn' from the Explorer window is good as well

on XP I would either use the real ImgBurn or there's a Microsoft command line utility called cdburn.exe that's part of the Server 2003 Resource Kit

[http://www.microsoft.com/en-us/download/details.aspx?id=17657](http://www.microsoft.com/en-us/download/details.aspx?id=17657)

You are absolutely right! Downloading ImgBurn properly now. Thank you!

---

### Post by Sonoran Desert Rat on 2012-09-10
:lolflag:  I had Nero on my computer the whole time! Der! The CD goes to the boot menu but it has errors. Marking this thread solved.

---

### Post by Sonoran Desert Rat on 2012-09-11
I am using Lubuntu right now, installed without erasing windows yet, from the cd. I used Nero to burn it to a brand new CD-R. 

Yay! \\:D/

Now I have some more learning to do ;)

---

### Post by Bashing-om on 2012-09-11
outstanding!
  Welcome to a wide open world of open source.

[INDENT]enjoy ubuntu <==BDQ

[/INDENT]

---

### Post by Sonoran Desert Rat on 2012-09-11
> **Bashing-om said:**
> outstanding!
  Welcome to a wide open world of open source.

[INDENT]enjoy ubuntu <==BDQ

[/INDENT]

Thanks! :D

---

### Post by anewguy on 2012-09-11
Suspected as much - glad it's working for you, and I also say welcome to ubuntu!

---

### Post by Sonoran Desert Rat on 2012-09-11
> **anewguy said:**
> Suspected as much - glad it's working for you, and I also say welcome to ubuntu!

Me too! 

:KSThank you everyone!:KS

---

