---
title: "laptop won start from USB stick"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by fotoflex on 2013-03-08
Hi,
my Toshiba Satellite P-110 Vista Home Premium packed it in a few days ago.
I used my Ubuntu live disc 10.10, which I had used earlier after a crash, again to  save some files.
And this time I even got the wifi working, so I can use it like a real laptop again.
So I tried to install Ubuntu, but that wouldn't work, the laptop cannot read either the origina lOS nor the Ubuntu.
Run it frum a USB stick, I thought, and followed the instructions via System - Administration - Startup Disc Createor.
I understand a USB keeps your settings and updates, etc, in fact, runs like a real OS.
I set the boot to FDD, but then I also get the message; 'Error, no such device'.
When I again open from the CD, I can see the stick contains everything it's supposed to.
Tried the same thing again, with the same negative result.
And now I'm stuck!
Any help is greatly appreciated, but please remember, I don't know anything about Ubuntu and hardly anything about Vista. :)

Thanks in advance,
Fotoflex

---

### Post by r3xu5 on 2013-03-08
Have you made the usb bootable?

---

### Post by fotoflex on 2013-03-08
> **r3xu5 said:**
> Have you made the usb bootable?

Thanks.
I followed all the steps in the startup disc creator, but I didn't come across an option for bootable or not.
'Startup Disc' sort of suggests Bootable to me, but I have to answer no.
So, how should I do that?

---

### Post by black veils on 2013-03-08
you dont want FDD, it has to be something else like USB HDD, or another menu from selecting HDD. If your system is capable of doing so hit the F12 key when the Toshiba  Splash Screen appears and select USB as the boot device.  The device has  to be plugged in PRIOR to powering up the system for the boot menu to  recognize it.

when you tried to create this persistent usb stick, did you download an .iso installer file for it?

you need a modern system really for security reasons. i would recommend [bodhi linux]("http://www.bodhilinux.com/") or [peppermint os]("http://peppermintos.com/") as they will be lighter, you dont want something heavy running from a usb stick unless maybe it is a 3.0 port.. both are based on ubuntu.

---

### Post by oldfred on 2013-03-08
My Toshiba Satellite came with XP and is about 6 years old. 
It boots from USB and from f12 (or is it f10?) one time boot key shows USB as a bootable option. But flash drive has to be bootable and plugged in before starting up.

---

### Post by fotoflex on 2013-03-08
[ATTACH=CONFIG]239929[/ATTACH]

thank you black veils,

but the Startup Disc Creator wants to erase the USB HDD before putting Ubuntu on it.
I don want to lose the files on the disc, and 1 TB seems a lot to me, just run Ubuntu?

I did not download an .iso installer for it,
I ran the live CD, read what I could about creating a startup stick on the internet, and then used the SDC.
When finished, it states that you can start up any computer like your own.
That seems a clear statement to me. :)

---

### Post by oldfred on 2013-03-08
But the startup installer erases the flash drive and it usually needs over 1GB to extract & install the ISO, the ISO is about 700MB. If you have data on that flash drive it may be time to buy another, they have dropped a lot in the last few years and larger ones  are now less than a $1 per GB.
You are showing an older version 10.10 that is not supported anymore. Much better to download 12.04 or 12.10. 

With my laptop I find 12.04 64 bit runs better than 10.10 did. If you have over 2GB of RAM then use 64bit.

---

### Post by fotoflex on 2013-03-08
> **oldfred said:**
> But the startup installer erases the flash drive and it usually needs over 1GB to extract & install the ISO, the ISO is about 700MB. If you have data on that flash drive it may be time to buy another, they have dropped a lot in the last few years and larger ones  are now less than a $1 per GB.
You are showing an older version 10.10 that is not supported anymore. Much better to download 12.04 or 12.10. 
With my laptop I find 12.04 64 bit runs better than 10.10 did. If you have over 2GB of RAM then use 64bit.

The USB Stick is empty AND erased before Ubuntu is installed.
It's 4 GB, I set the slide to 3 GB for the extra space allocated for settings.
So there's 1 GB for Ubuntu, that should be enough.
Black veil said I needed to use a USB HDD, that's what I responded to.

My laptop has SETUP (f2) or MULTIBOOT (f12).
But I can see a USB option there, only FDD, which is Flash Disk Drive, I think.

The hard disk is not available any more, that&#347; how all this started.

I had only 1GB RAM

Why would the stick not be bootable after installing?
And how do I change that?

I need the CD-player to run Ubuntu from, so I can't burn 12.04 or 12.10 to a CD.
Or can I download either and get them to the stick somehow?

---

### Post by black veils on 2013-03-08
you misunderstood, i meant usb hdd in bios. that did confuse me when you were saying about 1tb. ffd is floppy disk drive i think.

have you tried pressing F12 or something when booting the computer for one-time boot selection?

you can use the old cd of 10.10 to download ubuntu mini.iso which is a very small download. then use that startup disk creator to select the file and create bootable usb stick. the mini.iso relies on wired internet connection when installing. here is a guide (you can ignore the stuff about non-pae if it is not relevant though) [URL="http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html"]How To Install Ubuntu On Non-PAE Capable Hardware ~ Web Upd8: Ubuntu / Linux blog
[/URL]

---

### Post by fotoflex on 2013-03-08
> **black veils said:**
> you misunderstood, i meant usb hdd in bios. that did confuse me when you were saying about 1tb. ffd is floppy disk drive i think.
have you tried pressing F12 or something when booting the computer for one-time boot selection?
you can use the old cd of 10.10 to download ubuntu mini.iso which is a very small download. then use that startup disk creator to select the file and create bootable usb stick. the mini.iso relies on wired internet connection when installing. here is a guide (you can ignore the stuff about non-pae if it is not relevant though) [URL="http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html"]How To Install Ubuntu On Non-PAE Capable Hardware ~ Web Upd8: Ubuntu / Linux blog
[/URL]

Okay.
No, there'&#347; no option for USB HDD in the bios.
Can make a screenshot, sorry. :)
F2 lets me change the boot-order permanently, f12 for one-time.
Wired, is that absolutely necessary? Or just an advice?
Too much to explain, but I'm not on wired internet.

---

### Post by black veils on 2013-03-08
it should be necessary to use wired. you could try downloading a normal .iso then, but i dont know how well that will store in ram (using the live mode of your 10.10) but try it! 

for your hardware, i would recommend xubuntu for a lighter choice which is also not demanding on graphics. it can be made to look like almost anything.

---

### Post by fotoflex on 2013-03-08
Thanks,

to be sure, I need to download the first ([PC (Intel x86) desktop image]("http://releases.ubuntu.com/quantal/ubuntu-12.10-desktop-i386.iso"))
from this site and then use SDC to create the startup stick?

But, will that solve the problem of not booting?
I believe the computer ouldl run from the stick now, as long as it would boot.
The normal image file hasn't the same problem,you think?

[http://releases.ubuntu.com/quantal/](http://releases.ubuntu.com/quantal/)

---

### Post by black veils on 2013-03-08
get the 12.04 version as it is a long term support and meant to be more stable. or here is [xubuntu]("http://xubuntu.org/getxubuntu/") which is lighter and more appropriate for your hardware. then use startup disk creator to make the usb stick bootable.

your booting problem seems to be a bios issue. are you saying that the F12 key (or whichever it is for your computer) doesnt list the usb stick as an option? you need to plug in the usb stick before switching on the computer.

---

### Post by fotoflex on 2013-03-08
> **black veils said:**
> get the 12.04 version as it is a long term support and meant to be more stable. or here is [xubuntu]("http://xubuntu.org/getxubuntu/") which is lighter and more appropriate for your hardware. then use startup disk creator to make the usb stick bootable.
your booting problem seems to be a bios issue. are you saying that the F12 key (or whichever it is for your computer) doesnt list the usb stick as an option? you need to plug in the usb stick before switching on the computer.

The stick is semi-permanently fixed to the laptop.
Before, I used it for Readyboost.

But it doesn't show up under f12, no.
I can access it, and it shows up in SDC,, as you can see.

I will try the xubuntu-link.

Thanks again.

---

### Post by black veils on 2013-03-08
before you make the stick, maybe try opening gparted or disk utility and selecting the usb stick (make sure it is the right drive), and create new partition table, just in case it is corrupted and not being fixed by startup disk creator. in disk utility i think you only see the option of format drive/volume, no mentioning of partition table.

---

### Post by fotoflex on 2013-03-08
> **black veils said:**
> before you make the stick, maybe try opening gparted or disk utility and selecting the usb stick (make sure it is the right drive), and create new partition table, just in case it is corrupted and not being fixed by startup disk creator. in disk utility i think you only see the option of format drive/volume, no mentioning of partition table.

Gparted, where can I find that?

BTW, the download went straight to the location I downloaded something to before, without promting.:)
I assumed it would douwnload to the 'download-folder', because I had no choice.
But no, it had to be the HDD with not enough space. :)
I got a warning, but it won stopdownloading.
We'll see...

---

### Post by black veils on 2013-03-08
gparted may not be on the disc, so you will have to use disk utility.

strange it is not in the downloads folder, maybe it is in the main live disc user folder, it wont be on the hard drive or usb stick.

i have been trying to think of a way for you to get a system installed with the current limitations: outdated ubuntu cd, possible inability to boot from usb stick on that computer, cant make another cd/dvd because you are using the drive, cant use mini.iso as an installer as you have no wired internet - that seems likely to be an issue with any installer though, as it wont necessarily have the right driver support for your wireless.

is there no way you can fix the vista to create ubuntu disc etc?

Edit:
i am daft, for two reasons, one you said you just want to run a system from usb stick which makes me think you know the hdd died. two, you can buy a disc from here [http://www.osdisc.com/index.html](http://www.osdisc.com/index.html)

---

### Post by fotoflex on 2013-03-08
> **black veils said:**
> gparted may not be on the disc, so you will have to use disk utility.
strange it is not in the downloads folder, maybe it is in the main live disc user folder, it wont be on the hard drive or usb stick.
i have been trying to think of a way for you to get a system installed with the current limitations: outdated ubuntu cd, possible inability to boot from usb stick on that computer, cant make another cd/dvd because you are using the drive, cant use mini.iso as an installer as you have no wired internet - that seems likely to be an issue with any installer though, as it wont necessarily have the right driver support for your wireless.
is there no way you can fix the vista to create ubuntu disc etc?


If I could fix the Vista.........

I found Disc utility,
[Screenshot USB-Stick Utilities.png](http://wikisend.com/download/330386/Screenshot USB-Stick Utilities.png)
and that was were Gparted was also!
[Screenshot USB Stick Gparted.png](http://wikisend.com/download/519978/Screenshot USB Stick Gparted.png)
I told you I know nothing.

The file downloaded to a different Hard Disc Drive.
I downloaded some things to that disc earlier, but then I was offered a choice where to download to.
Not so this time. :(

It seems I need to have windows running, when I read this:
[http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)
Also that it will take 4.5 GB?!?
Which puts a stop to everything!

---

### Post by black veils on 2013-03-08
> **fotoflex said:**
> If I could fix the Vista.........

I found Disc utility,
[Screenshot USB-Stick Utilities.png]("http://wikisend.com/download/330386/Screenshot USB-Stick Utilities.png")
and that was were Gparted was also!
[Screenshot USB Stick Gparted.png]("http://wikisend.com/download/519978/Screenshot USB Stick Gparted.png")
I told you I know nothing.

The file downloaded to a different Hard Disc Drive.
I downloaded some things to that disc earlier, but then I was offered a choice where to download to.
Not so this time. :(

It seems I need to have windows running, when I read this:
[http://www.psychocats.net/ubuntu/usb](http://www.psychocats.net/ubuntu/usb)
Also that it will take 4.5 GB?!?
Which puts a stop to everything!

use gparted to right-click the /dev/sdb1 and unmount, then in menu >> device >> create partition table, click apply.
when done, right-click the unallocated space and choose 'new', choose FAT32 in the appropriate selector, ok it, then click apply.

now use startup disk creator to make the usb stick bootable with your new file. you need to browse to the file and make sure it is highlighted in the main window.

i would say try unetbootin (which can be used on Windows or Linux), but i dont think it will install on the outdated 10.10.

if i were you i would just order a live cd.

---

### Post by oldfred on 2013-03-08
A full install takes about 4.5GB but then you do not have any space for updates. 

If you can install grub to the flash drive, you can directly boot ISO without extracting them with grub2's loop mount. I use that on my Flash drives as then I can have more than one repair ISO and install ISO one one flash drive. Bit more complex as unetbootin or pendrive generally just work.

---

### Post by fotoflex on 2013-03-09
> **oldfred said:**
> A full install takes about 4.5GB but then you do not have any space for updates. 
If you can install grub to the flash drive, you can directly boot ISO without extracting them with grub2's loop mount. I use that on my Flash drives as then I can have more than one repair ISO and install ISO one one flash drive. Bit more complex as unetbootin or pendrive generally just work.

In the meantime I discovered I can download to any space with 'save link as' .
That I found out on the BBC website, where I download my podcasts from.
It discribes how to do just that.
So, Xubuntu is now downloading to a HDD with enough space.
To solve the boot-problem, I need to install Grub, to the USB Stick?

---

### Post by black veils on 2013-03-09
if you have used the startup disk creator, it will be all ready to use, its a matter of getting your computer to recognise it on boot via F12 one-time device selection.

---

### Post by fotoflex on 2013-03-09
> **black veils said:**
> if you have used the startup disk creator, it will be all ready to use, its a matter of getting your computer to recognise it on boot via F12 one-time device selection.

But, I used the sdc to make the stick from the live disc and it wouldn't boot up.
What is the difference with this? The. iso file?

---

### Post by oldfred on 2013-03-09
You only need to install grub to the USB flash drive if directly booting the ISO, not the normal extracted ISO the unetbootin and other installer create.

But if you have grub and more than one hard drive you can install from one drive to another. This is the same as installing grub to flash drive as flash drive is seen as another hard drive with most systems. The issue is making sure the path to the ISO file is seen by grub correctly as Ubuntu has not mounted any partitions, so the location is where it actually is on drive before Ubuntu mounts it.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)
may need this for some 
insmod iso9660
sudo umount -lrf /isodevice

I find installing from one hard drive to another to be very fast. And once you set up the grub & /iso folder, it is easy to change to a new version. I use it primarily for testing new ISO or test installs. But my new install from a hard drive to my newish SSD already partitioned took less than 10 minutes to install. Still more time to configure but a very fast install.

---

### Post by black veils on 2013-03-09
thats genius, although struggling to get my mind around it. so its do this or order a live cd. could they put grub on the internal hdd, telling it to boot the .iso on external 1TB hdd ? assuming the internal is somewhat dead.. which has not been clarified.

---

### Post by fotoflex on 2013-03-09
> **black veils said:**
> thats genius, although struggling to get my mind around it. so its do this or order a live cd. could they put grub on the internal hdd, telling it to boot the .iso on external 1TB hdd ? assuming the internal is somewhat dead.. which has not been clarified.

The internal Hard Drive is gone, fried like your brain yesterday! :)
But then irrevocably so.
There must be enough left inside to tell me that the computer cannot 'find this device', on starting up.
A new live cd would not solve my problem, I guess, for the laptop runs perfectly well on the cd I have I have now.
It's just that I can't get it to boot from the stick.
There is probably something else needed to do that.
Grub,I guess.
Do I understand correctly that I can also boot from the Hard Disc I downloaded to .iso to?
Must of my windows programs ran from my external disc, so I be happy to try that.
It's just that in the description they gave you could use the stick on any computer and run it as your own.
AND would keep all settings and updates.
According to the link in oldfred's post, as far as I can see, I would be running the 'try Ubuntu' and subsequently lose all settings every time I reboot.
 It would free up my cd player, though, so I could burn something again.

(Either of you ever played 100 Doors? It's a bit like that, isn't it?  ;-P )

Thanks again.

---

### Post by oldfred on 2013-03-09
With the live flash drive version you can turn on persistence. That allows some data to be saved if flash drive is large enough. But it has limits, you cannot update installer and partition to save into cannot be very large.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

   [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)


 With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)
      
 Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

    
      
 Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

---

### Post by fotoflex on 2013-03-09
The stick contains several files, among them BOOT -> GRUB -> LOOPBACK.cfg
So Grub is indeed already on there.
Thanks for the links, but it is all a bit too technical for me, I' m afraid. :(
I'll try and put 12.04 on the stick and hope for the better.

---

### Post by fotoflex on 2013-03-09
[Deamon.png](http://wikisend.com/download/490270/Deamon.png)

Sadly, another one scuppered!
The SDC can' t format the stick.
What is Deamon?
Maybe if I remove all files from it and try again?

Thanks.

---

### Post by Markup 001 on 2013-03-09
> **fotoflex said:**
> Hi,

I set the boot to FDD, but then I also get the message; 'Error, no such device'.
When I again open from the CD, I can see the stick contains everything it's supposed to.
Fotoflex

To go back to your original issue. Have you thought that your boot menu in your BIOS has probably got sub menus. I was helped sinilarly last week because I did not know this and could not locate the boot from USB option in my BIOS.

Try highlighting the FDD menu option and then hit enter rather than select and see if that gives you more options - such as USB - you can then toggle this up to 1st boot device and save the setting. I have a little eee pc and was not aware that the menus were stepped in this way until a forum user here pointed it out to me and sorted my booting issue.

It may help you, I hope so and good luck.

---

### Post by fotoflex on 2013-03-09
> **Markup 001 said:**
> To go back to your original issue. Have you thought that your boot menu in your BIOS has probably got sub menus. I was helped sinilarly last week because I did not know this and could not locate the boot from USB option in my BIOS.
Try highlighting the FDD menu option and then hit enter rather than select and see if that gives you more options - such as USB - you can then toggle this up to 1st boot device and save the setting. I have a little eee pc and was not aware that the menus were stepped in this way until a forum user here pointed it out to me and sorted my booting issue.
It may help you, I hope so and good luck.

Thank you, I didn' t know that either. :)
I' ll try that on the next boot.

---

### Post by fotoflex on 2013-03-10
No such luck!
Only HDD (which has a + in front of it) will show more options.
Not with ENTER, but ARROW RIGHT.
Pity, thanks for your help.

---

### Post by fotoflex on 2013-03-10
Well, I managed to put another file on the stick and that enabled me to erase it. :)
I then used the creator to make a 12.04 startup stick, but that isn't detected on startup either. :)
So, I'll keep on running from the cd.
It works, anyway.

Thanks for all suggestions.

---

### Post by fotoflex on 2013-03-10
Btw, I can download my podcasts, they are in MP3, but somehow the player says they are in an irrecognizable format.
Does Ubuntu produce a different MP3?

---

### Post by black veils on 2013-03-10
the problem is you must need mp3 support on the system (included with the restriced extras package), and various other things, but i dont think you can download it with the outdated version, even if you did, it would have to be repeated for each session.

---

### Post by fotoflex on 2013-03-10
Thanks,

I don't want to play them from the laptop, which actually works, but after I move the files to the MP3 player they don't.

---

### Post by fotoflex on 2013-03-14
Well, new Hard Disk installed.
So I was able to install 10.10 and to upgrade to 12.04.

---

### Post by black veils on 2013-03-14
you can burn a 12.04 installation disc now, best to do that in case something happens and you need to fix or install system.

---

### Post by fotoflex on 2013-03-14
> **black veils said:**
> you can burn a 12.04 installation disc now, best to do that in case something happens and you need to fix or install system.

Well, I had to do that to install it to start with!
So my future is safe. :P

One more question if I may,
how can I change from icons to list in a window?
I have files with over a 1000 photographs in them, and I need to select those by date.
Basic stuff, and I could manage it in 10.10, but I don't see the option here?

---

### Post by Vaspro on 2013-03-15
Check whether the boot configuration on bios setting is enabled and try it may help you some time

---

### Post by fotoflex on 2013-03-15
> **Vaspro said:**
> Check whether the boot configuration on bios setting is enabled and try it may help you some time

Thanks, but the bios does not give an option to boot from an USB stick.
In the meantime, i've put in a new, bigger hard disk and doubled the RAM, and the laptop boots up from there.
(But it doesn't run any faster than from the CD. :( )

---

### Post by black veils on 2013-03-15
i dont know if this is still relevant because i know nautilus has lost features [http://askubuntu.com/questions/134371/how-do-i-set-default-view-to-list-in-nautilus-file-manager/134380#134380](http://askubuntu.com/questions/134371/how-do-i-set-default-view-to-list-in-nautilus-file-manager/134380#134380)
i think you want detailed view though, if it is an option.

as for speed of your system, are you using xubuntu? if no, you should try it, because ubuntu uses the unity desktop which is heavier.

---

### Post by oldfred on 2013-03-15
I use fallback or gnome-panel in 12.04 and it is almost the same as 10.10 and seems a tad faster than 10.10 was. Have not used Unity enough to know it it worked or not.

In Nautilus it is edit, preferences and there are several tabs with settings. 

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo (top right) and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

### Post by fotoflex on 2013-03-15
Thanks, black veils & old fred,

I thought I used xubuntu, but since the laptop displays Unity (a load of icons on the left), I must have done something wrong.
I tried so many things over the last couple of days, I must have lost track at some point.

I also tried to re-install Vista, which should have worked with a new hard disk,
but NOT if you use a USB-cd rom player!
And no work-around, neither, you MUST use the build-in cd player. (Which is broken.)
After that dissapointing episode, I installed 12.04.
I also installed Wine, with which I opened two of my indispensibe programs. 
And they worked! Once.
The second time the programs had to close down for some reason.
Pity, for I just ripped a one-hour television program from dvd, that I recorded yesterday.
I used OGMrip.
That took over nine hours instead of the one hour I'm used to.
That is really long, and none of the options I'm used to.
OGGConvert is now busy converting it to a reasonable size, which takes 2 hours,
another 12 minutes to go.

After that I'll restart the computer in the hope that it will display Gnome,
for it doesn't on re-loggin in ( re-inlogging?).
The icon after my user name shows the little footprint however, so I live in good hope.

PS, I used the extra time to check, definitely Xubuntu:
  /media/Elements/Xubuntu/xubuntu-12.04.2-desktop-i386.iso

PPS, conversion finished! No sound!

---

### Post by fotoflex on 2013-03-15
Nah, didn't work.

---

### Post by fotoflex on 2013-03-15
Late at night, but good news:
after another reboot, it works!
But strange; when I open a window, it doesn't show the options, but when I reopen it, it does.
The laptop is sort of slowly building up to it. :)

One problem solved, any suggestions for the others?

---

### Post by fotoflex on 2013-03-18
And to return to the original subject, today I had the opportunity to test the USB Stick on another computer.
That ran perfectly!
So, for some reason the stick won't run NOT on the computer I made it with.
That's too much exeptions to the rule for a noobie. :(

---

### Post by oldfred on 2013-03-18
Difference with computers is usually video issue, but could be other drivers that special boot options. 
Easiest way may be to search for others with same computer and see if they posted details of how they made it work.

---

### Post by fotoflex on 2013-04-04
So I'm running Ubuntu now, and I managed to get my Xilisoft Ripper and the Converter working with Wine.
And they also take hours to rip or convert, just like Oog and ::rip, etc.
Since they used to do it much, much quicker when I was running Windows, it must be a Ubuntu-thing.
Emailing is a lot quicker now, but I rather had it the other way around. :(

---

