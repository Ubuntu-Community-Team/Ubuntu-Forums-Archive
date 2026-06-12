---
title: "Attempting to put Xubuntu on new PC but CD doesn't load"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by queazy03 on 2013-04-20
Hi.

I'm a complete beginner with Ubuntu / Linux OS types, and am trying to install Xubuntu on new PC but the CD doesn't work.  

On the same PC's new hard drive Xubuntu was previously successfully installed last week, but never used.  Then I took out the old IDE hard drive, put in new motherboard + CPU, and Xubuntu doesn't work anymore.  Now I'm trying to install with Xubuntu boot CD and that doesn't work either.

Here is a picture regarding my problem at 
"[http://imgur.com/vIUQri1](http://imgur.com/vIUQri1)"


[LIST]
[*]A0) This is the process in how I made the Xubuntu boot CD 
[*]A1) Downloaded via torrent the "xubuntu-12.10-desktop-i386" ISO from "http://xubuntu.org/getxubuntu/" 
[*]A2) Downloaded & installed "ImgBurn" software to burn ISO to CD 
[*]A3) Chose "Write Image File To Disc" option to burn CD. 
[*]A4) Have done step "A3" several times to try to burn CD at slowest possible burn speed, which seems to be 10x, to ensure CD is readable.  Choosing any slower speed with ImgBurn software just bumps the writing speed back up to 10x speed. 
[/LIST]

I'm quite certain I am choosing the correct boot device, the CD drive, to be booted from.  When the computer powers up and I press F11, I am given three choices as to how the computer should boot up.  
[LIST]
[*]1st Choice is "UEFI: Built-in EFI Shell"...I have no idea what this is. 
[*]2nd Choice is "AHCI P2:  Hitachi HDS721050CLA36", this should be the hard drive 
[*]3rd Choice is "AHCI P0:  HL-DT-ST DVDRAM GSA-H6", I'm quite certain this is the CD drive, and I choose this as primary boot device. 
[/LIST]

Just to make sure I'm not doing something completely wrong, here are my hardware information.  If Xubuntu can not run on these parts for whatever reason, please tell me.
[LIST]
[*]MotherB[FONT=arial]oard:  [/FONT]ASRock FM2A75M-DGS FM2 AMD A75 (Hudson D3) 
[*]CPU:  AMD A8-5500 Trinity 3.2GHz (3.7GHz Turbo) Socket FM2 
[*]Hard Drive:  500 GB internal SATA Hard Drive, Hitachi Deskstar 7K1000.C HDS721050CLA36 
[*]CD Drive:  HL-DT-ST DVDRAM GSA-H6 (best as I can tell).  This is the only part that's old in this list, rest were freshly installed this week. 
[/LIST]
I can also list my Ram type plus CPU fan if requested, but I doubt that information would be useful.


Previously this computer had a different motherboard, an additional IDE Hard Drive, CPU & RAM and somehow I was able to successfully install Xubuntu onto that (installing onto new 500 GB internal SATA Hard Drive that is still used).  However now after I had replaced all the old parts I am trying run the Xubuntu OS off the Sata hard drive still there, and it doesn't work (see right side of above mentioned picture).  I try to make a fresh Xubuntu install, but I lost the CD I hard originally burned.  Now I have burnt around seven new Xubuntu boot CD's, but they all give me errors.  

I don't know what to do to install Xubuntu onto the machine anymore, please help.  Thank you.

---

### Post by Impavidus on 2013-04-20
That you can't boot from the old hard drive may be because of a change from BIOS to UEFI. I don't know much about that, but it may cause problems. Maybe you can switch it to legacy mode. Also, check your RAM. Maybe it isn't properly plugged in. The "Unable to find a medium containing a live file system" error suggests the the live disk can't access your RAM. And unless you have a tiny amound of RAM compared to the other specs of your computer I would use the 64 bit version of Xubuntu. Can you provide the details on your RAM?

---

### Post by queazy03 on 2013-04-21
> **Impavidus said:**
> That you can't boot from the old hard drive may be because of a change from BIOS to UEFI. I don't know much about that, but it may cause problems. Maybe you can switch it to legacy mode. Also, check your RAM. Maybe it isn't properly plugged in. The "Unable to find a medium containing a live file system" error suggests the the live disk can't access your RAM. And unless you have a tiny amound of RAM compared to the other specs of your computer I would use the 64 bit version of Xubuntu. Can you provide the details on your RAM?

Hi  

1) The type of RAM I have is "G.SKILL Value Series 4GB 240-Pin DDR3 SDRAM DDR3 1333 (PC3 10600) Desktop Memory Model F3-10600CL9S-4GBNT"

I will try to use the 64 bit version of XUbuntu.  

Question 1:  What is "UEFI"?  As in "because of a change from BIOS to UEFI"?
Question 2:  What is Legacy mode?

Also, I had an old IDE hard drive, that I tried to install Xubuntu onto, but it somehow it couldn't be installed.  So I removed that old hard drive completely, it is no longer installed in the PC at all.  The new SATA hard drive is still there, which Xubuntu was successfully installed on, but after I put in new Motherboard + CPU it doesn't work.  

Looking forward to any advice, thank you very much.

---

### Post by BlinkinCat on 2013-04-21
Hi,

Re question 1 -

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Good luck

---

### Post by pqwoerituytrueiwoq on 2013-04-21
your 1st mistake is using the 32bit version, you should use the 64bit one (amd64)
you can use a flash drive 1gb capacity or more, you can set it up using unetbootin (google it)
13.04 comes out on the 25th i see no reason to install 12.10 just to upgrade in less than a week
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-amd64.iso) (800MB)

---

### Post by AndyOpie150 on 2013-04-22
Even if the system is a 32bit, but has 4GB of RAM then the 64 bit install is recomended. 32 bit with 2GB or lower of RAM need the 32 bit install.

I like to use PennDrive USB creator or LiLi USB creator (Linux Live). Much more reliable in my opinion (installed and tried more than 2 dozen distro's using them).
This will require you to change the boot order in the BIOS, or (if you still can't boot into USB drive) install Plop Boot Manager.

---

### Post by queazy03 on 2013-04-22
*EDIT*
HOLY CRAP

Look at this "http://imgur.com/qotc5Bj"!!
What does this mean?  Is this why my RAM isn't working, preventing me from installing Xubuntu?  I'm at 1,300,000+ million errors now!!
All I did was choose the "Memory Test (memtest 86+)" option when I got to the right middle part of what is in the picture here at "http://i.imgur.com/vIUQri1.jpg".


Previous unedited post is below
-----------------------------------------------------------------
Hi, I tried installing with the 64bit version of Xubuntu, and it didn't work then either.  I got the same error as before, which is in the bottom left of the picture at "http://i.imgur.com/vIUQri1.jpg".  

Also, I double checked to make sure that the DDR3 RAM stick was properly inserted, from the looks of it the stick seems to be properly installed, however there is only a single stick of RAM.  Do I need two to make the machine function properly?  It was a $28 stick, so I thought I would be ok with just one, but if I need to buy a second RAM stick for the computer to work properly I will.  

I'm going to try to install with the USB stick next and tell you guys how that goes.  Thank you.

---

### Post by Cheesemill on 2013-04-22
Looks like your RAM is faulty.

Send it back and get a replacement.

---

### Post by pqwoerituytrueiwoq on 2013-04-22
**IMPORTANT:** If that it the memtest on the 12.10 disk image there is a bug at random number sequences that makes everything read bad
use the version on raring or get it from [http://www.memtest.org/](http://www.memtest.org/)


edit:
put your ram into manual clock mode settings according to the manuf. specs (you can call them and they will help you)

i have seen some systems report the ram wrong like what you are seeing in memtest 86 there, if you notice it says ddr2 ram
edit:
dam ram prices have gone up, it was $40 for a 8gb kit of ddr3 1600 cl9 and about 22 for a single stick
a a8 APU can utilize 1866 ram, dual channel is best
for a A8 APU i recommend an 8gb kit (2 sticks) of ddr3 1600 or 1866

---

### Post by queazy03 on 2013-04-25
Hi!  
It turns out my previous problem was the BIOS / UEFI thingy had not been updated with the new installed hardware (which had new DDR3 type RAM).  So when I did the Memory test, it was off of the Xubuntu that was installed with the old hardware that was no longer connected, including old DDR2 type RAM.  So when the Memorty test tried looking for this DDR2 RAM and couldn't access it, it gave me the error.  I just put in the CD and installed Xubuntu from there and everything went fine.  

However, today I'm trying to install that new Xubuntu "Raring Ringtail" and am getting problems again, although they are different.  

The problem is 
1) I don't know whether to tell my UEFI to choose to boot off the "UEFI DVD" or "AHCI DVD", I don't know the difference.
2) I've tried booting off both the UEFI DVD & the AHCI DVD, trying both so that the computer boots off of the Xubuntu Raring Ringtail install boot DVD I put in there...and no matter which I choose the screen goes black after a while and just stays black for 10+ minutes.  

What can I do?  What am I doing wrong?  Thank you.

---

### Post by pqwoerituytrueiwoq on 2013-04-26
i have seen it boot with the screen saver running before, did you move the mouse or hit a key before cutting the power?
AHCI refers to the sata controller's mode
UEFI refers the the boot method that supports really large HDDs (>2TB)
did you read my last post?
Which AsRock motherboard are you using?
i know it is a FM2 socket but that is it
have you tried booting a flash drive setup with unetbootin?

---

### Post by queazy03 on 2013-04-26
Hi,

You aren't going to believe this, but the problem was the monitor!  I was plugging it into an older 3:4 monitor, and somehow was going over its resolution limit and therefore the screen was not displaying anything.  I plugged in a newer 16:9 monitor and was able to install Xubuntu Raring Ringtail just fine now.  I'll have to figure something out to get that older (and larger) screen working.  

I still have no clue how to use Xubuntu, but I've been able to get onto the internet and watch youtube, so that's a start.

Ultimately this PC will not be for my use, but for other family members, so I'm trying to keep things simple for them.

_**Question:**_  How do I make a shortcut for Firefox to go on the desktop?  Every Time I've done something, I end up with a error saying "this isn't a trusted application, Launch anyway or cancel?" type of error.  I will need this to be a simple "double click, go to internet" type deal, how can I achieve that?  Thank you.

> **pqwoerituytrueiwoq said:**
> i have seen it boot with the screen saver running before, did you move the mouse or hit a key before cutting the power?
[COLOR=#ff8c00]*Yes, still no effect on monitor, until I plugged in a different monitor that happened to be a newer 16:9 model.*[/COLOR]
AHCI refers to the sata controller's mode
UEFI refers the the boot method that supports really large HDDs (>2TB)
[COLOR=#FF8C00]*So I should boot up with AHCI then, right?  My hard drive is only 500gigs.*[/COLOR]
did you read my last post?
*[COLOR=#ff8c00]Read it, but still do not completely grasp all the concepts.  I did update the BIOS / UEFI thing and told it to detect hardware & set it to default parameters  and that seemed to have fixed the bulk of the trouble.  [/COLOR]*
Which AsRock motherboard are you using?
i know it is a FM2 socket but that is it

[LIST]
[*][COLOR=#ff8c00]*_MotherBoard:_  ASRock FM2A75M-DGS FM2 AMD A75 (Hudson D3) SATA 6Gb/s USB 3.0 Micro ATX AMD Motherboard*[/COLOR]
[*][COLOR=#ff8c00]*_RAM MEMORY _<NEW bought Tuesday>: Patriot Signature Line DDR3 2x4 GB PC3-12800 1600MH*[/COLOR]
[*][COLOR=#ff8c00]*_CPU:_ AMD A8-5500 Trinity 3.2GHz (3.7GHz Turbo) Socket FM2 **65W Quad-Core Desktop APU (CPU + GPU) **with DirectX 11 Graphic AMD Radeon HD 7560D AD5500OKHJBOX*[/COLOR]
[*][COLOR=#ff8c00]*_CPU FAN:_ COOLER MASTER Hyper 212 Plus RR-B10-212P-G1 **"Heatpipe Direct Contact" Long Life Sleeve **120mm CPU Cooler Compatible **with Intel 1366/1155/775 and AMD FM1/FM2/AM3+*[/COLOR]
[*][COLOR=#ff8c00]*_Graphics Card_ (old): ASUS EAH4350 Silent DI 512MD2 (LP) *[/COLOR]
[*][COLOR=#ff8c00]*_Hard Drive:_    Hitachi Deskstar 7K1000.C HDS721050CLA36 **500 GB,Internal,7200 RPM,2.5" **(0F10381) Hard Drive*[/COLOR]
[*][COLOR=#ff8c00]*_CD DRIVE:_    HL-DT-ST DVDRAM GSA-H6*[/COLOR]
[/LIST]
have you tried booting a flash drive setup with unetbootin?
[COLOR=#ff8c00]*No, I don't know how to setup a boot USB-Stick.  **I did try to research it, but it seemed complex and unfamiliar to me so I tried other alternatives.  **But I suppose it is a moot point now as I was able to load it off the boot DVD.*[/COLOR]

---

### Post by pqwoerituytrueiwoq on 2013-04-26
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) makes it easy to setup a flash drive to boot

as far as my last post on page 1, when you ran memtest using the 12.10 cd/dvd there is a bug in that memtest that makes give everything errors when it reaches test 7 (random number something)

is there a option in your bios about uefi and bios? if it is on bios i think it will boot no issue
if you can boot a Windows XP install disk, that is not the issue (if that is easier to check)

take that GPU out you will get better GPU performance from the GPU on the A8-5500

Why put a high end cooler on a locked 65W CPU? the stock cooler would have been fine

---

