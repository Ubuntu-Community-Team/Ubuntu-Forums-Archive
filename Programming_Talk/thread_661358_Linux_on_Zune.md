---
title: "Linux on Zune"
date: 2008-01-07
forum: Programming Talk
---

### Post by YodaMstr on 2008-01-07
Ok, so, as it stands I barely use my Zune.  I hate to say it, but I just rarely have the time to walk down the street with MP3 player charged and in tow.  So, if anyone would care to help, I'd be willing to void my wonderful warranty to try and get Linux on Zune.  I just have no technical knowhow as to how I could pull it off.  So if anyone wants to help, even if it's just to say "nope, that won't work", then I'll be glad to sacrifice my music player.  I just think the WiFi aspect would be a nice reason to port Linux onto it. :P

So, any takers or suggestions?

---

### Post by t3hi3x on 2008-01-07
What version of it do you have? Wikipedia said it had some version of windows on it...meaning it may have an x86 processor on it...doesn't guarantee that, as the xbox 360 has windows on it and its PPC.

Anybody know info about the architecture? This is very important with compiling the kernel for the proc.

---

### Post by t3hi3x on 2008-01-07
More than enough info:

    *  30 GB 1.8-inch hard drive (Toshiba)
    * Support for a variety of music, video, and picture formats including MP3, ASF, WMA, WMV, MP4, MPEG-4, JPEG, and AAC'
    * 3-inch QVGA LCD display, 65k color
    * Radio Data System (RDS) enabled FM receiver
    * Integrated 802.11b/g WiFi
    * Up to 14 hours of audio playback, 4 hours of video or pictures (under optimal conditions)
    * 4.4 × 2.4 × 0.58-inch (11.2 × 6.1 × 1.4 cm)
    * 5.6 ounces (158.8 grams)
[COLOR="Red"]    * CPU: Freescale i. MX31L processor; ARM Core, FPU (SCIMX31LVKM5 / 3L38W / CTAU0629)[/COLOR]
[COLOR="Red"]    * RAM: 64 MBytes x32 Mobile SDR DRAM / 133 MHz / 90 mA (K4M51323PC-DG75)[/COLOR]
    * Flash: 2 MBytes NOR flash, 3.3V, 1Mx16 Boot block (PH28F160C3TD)
    * TV-out
    * USB 2.0
    * Included in the box: earphones, USB data cable, carrying pouch

These things will need drivers compiled as well with the kernel.

# ATA driver (?): 8-bit bus transceiver/driver (P003 / 620A5)
# Wi-Fi: RF/BB/MAC 802.11g Wi-Fi (KeyStream) module (KS3021 / KS7010) 
# FM Tuner: Silicon Labs Si4701 single-chip radio tuner (4701A15)

I'm not familiar with actually compiling it, but it's worth a shot. I know there are many on this form that are familiar with compiling Linux for other architectures. But those drivers will have to exist or be created for them to work.

The big ones are the sound card, the ATA driver, and anything else you want to work.

---

### Post by YodaMstr on 2008-01-07
Yes, I have the original Zune, with the freescale processor.

For clarification:
[IMG]http://www.zunerama.com/graphics/zune-version-brown.jpg[/IMG]

So, any ideas?  I'm willing to try anything, as long as it leaves my Zune somewhat salvagable afterwards. =P

---

### Post by tgalati4 on 2008-01-08
If you rub it, it will get shiny. 

There have been attempts to put Linux on it, but the firmware is encrypted.  Without knowing the hash to follow the firmware boot, it's difficult to intercept the firmware boot and substitute your own.  A google search will show what has been done to date, but to my knowledge, the encryption is a real show stopper.  The hardware is good and shouldn't be too difficult a challenge once a method is discovered to substitute firmware.

---

### Post by Zune-Online.com on 2008-01-08
The Zune-Linux project is hosted on zune-online.com . Although I'm not related to the project, I can verify the problem is to bypass the Zune protection system and and boot linux on it. Microsoft has done a good job and its protecting it with digital signatures and certificates.

Until someone will find a way to bypass it...
[http://www.zune-online.com/forum/zune-linux-project-news-b16.0/](http://www.zune-online.com/forum/zune-linux-project-news-b16.0/)

Kostas

---

### Post by silverbyte1 on 2008-01-18
sorry to resurrect an old thread... 
however, please take a look at this:

[http://sourceforge.net/mailarchive/forum.php?thread_name=9dbbf8f60712271644m66e1fa8g3a1116c056456eb4%40mail.gmail.com&forum_name=libmtp-discuss](http://sourceforge.net/mailarchive/forum.php?thread_name=9dbbf8f60712271644m66e1fa8g3a1116c056456eb4%40mail.gmail.com&forum_name=libmtp-discuss)
This is an attempt to make "libmtp" to access Zune from linux (potentially portable to Win as well). Currently, the status is that libmtp (via Amarok) can browse ur Zune and even delete music.
But it is unable to sync music, unless of course there is a VmWare windows with Zune-software running.

This is due to certain handshaking that takes place between Zune and the computer - strictly speaking this is NOT mtp, but rather some non-standard zune-specific protocol extensions called MTP-Z.

The author of libmtp is asking for help in this authentication- authorization schemes.

Could anybody help?

---

### Post by Exurion on 2009-01-24
so, i has a Zune 30 gig, and i wanna put linux on it (can we say Zubuntu?) mostly because i have linux on my machine(using windows right now, but still love linux :P)  and i want to utilize the wi-fi feature of the zune to it's fullest capability...  mostly web browsing...  if anyone's been keeping up with zune good-ness, there is "improved" wifi stuffs, and the ability to build apps and games for it by yourself...  so what if there was a linux app for the zune, like the linux .nds file for the DS linux?

---

### Post by spartan777 on 2009-01-28
assuming you've read all the previous posts, I don't think anything has changed.

---

### Post by DivinityX on 2009-02-08
Yeah, I thought that with the new updates for Zune there should at least be a Ubuntu app. Hopfully someone is still working on the Linux on Zune project...I at least want to update my Zune via linux. (Wine doesn't work)

---

### Post by novafluxx on 2009-03-19
Seems that, thought wine has come a long way, we all still should keep a nice virtual machine around of Windows!

Use VirtualBox, take a snapshot, you'll never need to activate it, and you can do whatever you need :-):popcorn:

---

### Post by grungedoobie on 2009-03-31
Hmm, Have you guys seen this page?

[http://hackaday.com/2006/11/14/zune-gutted/comment-page-2/#comment-68287](http://hackaday.com/2006/11/14/zune-gutted/comment-page-2/#comment-68287)

The hard drive is a 1.8" ata-6 micro drive.  I'd almost bet that most if not all of the junk that keeps the Zune a useless WMD (Windows Media Device) is in the software on the drive, and is implemented at boot.

Might there be a way to pull the drive and hook it to a computer via an ide converter and just format the hard drive with what linux needs to boot?

The I/O port has USB capability right?  It also has Wi-Fi right?

All I'm saying, is there ought to be a way to do something so that the Zune can be made useful.  There's a lot of hardware in there.  What a waste.

Oh well.  I've been haggling with this Zune junk for too long.  (Since Christmas)  I'm tired of it.  Thanks again Microsoft, for another pretty door stop that can be used as a rechargeable flashlight.

The Grunge

---

### Post by jordan420 on 2009-04-25
I agree. i would like to actually use my zune. better google more see if theres anything...

---

### Post by aromo on 2009-05-02
Anybody successful using Amarok or libmtp to sync a Zune in Ubuntu?  One was handed to me and I do not want to create a virtual machine just to load music in it.

That's MS, they always want you to run their (often) crappy software.

---

### Post by jordan420 on 2009-05-11
once upon a time i had an archos media player. it was a nice device.. it packed a laptop harddrive whatever the technical term is i dont know. but anyway they had a security feature built into the firmware that refused to mount a foreign harddrive. I dont know if you have ever seen one of the things but the harddrive is so accessible you almost think its made to be switched out. but yeah. i think if a smaller company like archos uses such a security measure you can bet that Microsoft does. being the evil corporation that they are. If anyone knows better please post!!

---

### Post by Alestan on 2009-05-27
Okay, someone with more Linux smarts than me, check this page out.
[http://gizmodo.com/gadgets/portable-media/how-to-use-the-zune-as-a-hard-drive-217024.php](http://gizmodo.com/gadgets/portable-media/how-to-use-the-zune-as-a-hard-drive-217024.php)
From what it says, it lets you get direct access to the Zune's hard drive.  Maybe you could format it from there and put a bootloader on it.  It would bypass the encryption, if that does indeed work.  Anyway, if it works, please let us know, I'd love to have the portable Linux install.

---

### Post by grungedoobie on 2009-05-27
> **Alestan said:**
> Okay, someone with more Linux smarts than me, check this page out.
[http://gizmodo.com/gadgets/portable-media/how-to-use-the-zune-as-a-hard-drive-217024.php](http://gizmodo.com/gadgets/portable-media/how-to-use-the-zune-as-a-hard-drive-217024.php)
From what it says, it lets you get direct access to the Zune's hard drive.  Maybe you could format it from there and put a bootloader on it.  It would bypass the encryption, if that does indeed work.  Anyway, if it works, please let us know, I'd love to have the portable Linux install.

Yes, please follow the thread below that link.  Nobody can get it to work properly, or say how to make it work properly.  I'm thinking someone found a loophole in registry to allow you to connect to the device and Microsoft quickly made an update to close or at least taint the loophole.

---

### Post by xzero1 on 2009-05-27
Microsoft got burnt when someone used a logic analyser to figure out how to get by the original xbox security.  I'm sure they beefed up their security a bit for the zune. But why would microsoft want it to run under linux. It a good thing [our courts say] microsoft is not a monopoly.

---

### Post by Alestan on 2009-05-27
> **grungedoobie said:**
> Yes, please follow the thread below that link.  Nobody can get it to work properly, or say how to make it work properly.  I'm thinking someone found a loophole in registry to allow you to connect to the device and Microsoft quickly made an update to close or at least taint the loophole.

So then might an old Zune work?  One untainted by Macroshaft's patch?  I am looking at getting one, and I have already ordered a 1.8" drive to mini usb converter.  Worst case I can pull the hard drive and install it that way.

---

### Post by xzero1 on 2009-05-27
>  Worst case I can pull the hard drive and install it that way.
Very unlikely. The drive is probably locked and I'm sure microsoft's firmware or even hardware will check if it has been tainted and shut down if not disable the device.

---

### Post by tgalati4 on 2009-05-27
Based on my experience with a nokia n800 that runs linux on an arm processor, you need some method to flash new firmware over USB.  The firmware does a miniboot to control charging and check disk integrity.   MS has tight control over this firmware.

Of course you could find a used nokia n800 and save yourself a lot of grief.  Sell your brown zune to the unwashed masses.

---

### Post by xzero1 on 2009-05-28
> Currently, the status is that libmtp (via Amarok) can browse ur Zune and even delete music.They must be using this in Jaunty. I have a 30G zune and Ubuntu mounts it without Amarok. Still can't play anthing.

---

### Post by jordan420 on 2009-06-22
man its totally useless still though.. and the software for zune.. it really is a piece of work. i swear it will go through my music and randomly select songs that it wants to sync. doesnt matter what i want it to micro$oft apparently does my thinking for me now... even in terms of music.:(

---

### Post by discord on 2010-01-26
MTPz needs to be reverse engineered. This takes developers. I suggest you vote on getting zune support with double twist. They would have to get through the MTPz handshake to do this.

[http://forums.doubletwist.com/default.aspx?g=posts&m=6724&#post6724](http://forums.doubletwist.com/default.aspx?g=posts&m=6724&#post6724)

---

