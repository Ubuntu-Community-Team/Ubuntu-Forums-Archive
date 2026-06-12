---
title: "New to Ubuntu, need help with netbook"
date: 2012-08-15
forum: New to Ubuntu
---

### Post by ThursdayNext on 2012-08-15
I am also pretty new. I've looked all over the forums, and what isn't utterly confusing isn't particularly helpful either. Rather than bother people in the threads, I messaged a couple of people who seemed to be on a lot and asked them for help, about a month ago. I haven't heard from them.

I am so deeply unhappy with ubuntu. I put it on a little emachines 250 netbook about 5 months ago, but everything I needed to do seemed to need a brand new steep learning curve, and took an amazing amount of time to research every install command, assuming the crowdsourced installation instructions even had complete information. And it's that which seems to have bricked the little netbook. I followed uninstall instructions. Windows (a dual boot) still worked. I resized the partition. I restarted. Now all I get is <grub rescue>. Now, way too late, the instructions say I should've removed something else. Great, thanks for that now.

I can get to the bios, but it will not boot off ubuntu on the stick, which is how I first installed it. It is a netbook, and so does not have an internal cd drive, and did not come with a separate rescue cd. I have a live windows cd, but it will not boot off an external cd/dvd player.

this has been a nightmare. I just wanted this little netbook to be able to be able to monitor a group room at work as a webcam, and allow people to contact me from there via something like ichat.

Is there absolutely nothing I can do with what was a nice little useful piece of equipment? It's been so awful with ubuntu that I'll take windows. Thanks if you've got anything helpful for me, I'm pretty disillusioned.

---

### Post by cogier on 2012-08-15
Hi Thursdaynext,

You will get better help if you provide the Forum with more info regarding the computer you wish to install Ubuntu on.

There will be someone out there who will have the necessary knowledge.

---

### Post by oldos2er on 2012-08-15
Post moved to its own thread.

---

### Post by BrianBlaze on 2012-08-15
> **ThursdayNext said:**
> I am also pretty new. I've looked all over the forums, and what isn't utterly confusing isn't particularly helpful either. Rather than bother people in the threads, I messaged a couple of people who seemed to be on a lot and asked them for help, about a month ago. I haven't heard from them.

I am so deeply unhappy with ubuntu. I put it on a little emachines 250 netbook about 5 months ago, but everything I needed to do seemed to need a brand new steep learning curve, and took an amazing amount of time to research every install command, assuming the crowdsourced installation instructions even had complete information. And it's that which seems to have bricked the little netbook. I followed uninstall instructions. Windows (a dual boot) still worked. I resized the partition. I restarted. Now all I get is <grub rescue>. Now, way too late, the instructions say I should've removed something else. Great, thanks for that now.

I can get to the bios, but it will not boot off ubuntu on the stick, which is how I first installed it. It is a netbook, and so does not have an internal cd drive, and did not come with a separate rescue cd. I have a live windows cd, but it will not boot off an external cd/dvd player.

this has been a nightmare. I just wanted this little netbook to be able to be able to monitor a group room at work as a webcam, and allow people to contact me from there via something like ichat.

Is there absolutely nothing I can do with what was a nice little useful piece of equipment? It's been so awful with ubuntu that I'll take windows. Thanks if you've got anything helpful for me, I'm pretty disillusioned.

Okay I guess my first question is why you can't do what you want to do with windows lol... but since this is a linux forum I would like to know your PC specs :)

---

### Post by na5h on 2012-08-15
If you have a backup of your files, a fresh install is usually the easiest way to go!

---

### Post by I2k4 on 2012-08-15
Mystery problem?  Mystery girl:

[http://www.thursdaynext.com/index2.html](http://www.thursdaynext.com/index2.html)

---

### Post by ThursdayNext on 2012-08-15
To answer the person who wondered why I didn't just use windows, originally this netbook was for my daughter, and she was on the internet a lot, and I didn't want to deal with viruses, so I installed ubuntu. She's  moved on, and I wanted to get some use out of the netbook.

All I can tell you about the system is what i can read on it, or in bios:
emachines
intel atom N270
Designed for Windows XP
10.1 lcd screen
1 gb memory
160 gb hdd
3 cell li-ion battery

cpu type: intel Atom Cpu n270@1.60ghz
cpu speed 1.6-hz

hdd model name: Hitachi HTS543216L9A300
HDD serial number: 091105FBC206VCHKG2WC
System Bios Version: V1.25
VGA Bios Version : Intel V1484
Serial Number: LUN970B993993264581601
Asset Tag Number:
Product Name: eM250
Manufacturer Name: eMachines
UUID: OC4726E744B86467705AB61682DA


Main:
Total Memory 1024 MB
Video Memory [8MB]
Quiet boot [enabled]
Network Boot [enabled]
F12 Boot Menu [enabled]
D2D recovery [enabled]
SATA Mode [AHCI]
Fast Boot [enabled]

Security, everything on clear, no password to power on

Boot priority order
1. USB CDROM:  
2. IDE0: Hitachi HTS 543216L9A300
3. IDE1:
4. USB FDD:
5. Network Boot: Atheros Boot Agent
6. USB HDD:



And every time I turn it on, I get a quick flash by the bios screen then

error: no such partition.
grub rescue>

I have no idea what of the above is important, and I know what about 40 percent of it means. But now you know absolutely everything I know about this computer.

Oh, so I have the original ubuntu stick. In bios, I saw USB HDD change to USB HDD: Staples (which is the brand name of the stick with the loadable ubuntu). Change the bios so that is the first boot and. . .
error: no such partition.
grub rescue>

I've put the windows iso disk in a usb disk drive (the netbook has no internal drive) and got a blank in bios under USB CDROM, then. . .
error: no such partition.
grub rescue>

thanks all

PS, here's something that's the first hopeful thing I've seen all month:
if I type in ls
I see
(hd0) (hd0.2) (hd0.1) (hd1)
no idea what it means, but it's the only thing besides grub rescue that I've seen.

---

### Post by audiomick on 2012-08-15
> **ThursdayNext said:**
> 
I can get to the bios, but it will not boot off ubuntu on the stick, which is how I first installed it.

> **ThursdayNext said:**
> 
Boot priority order
1. USB CDROM:  
2. IDE0: Hitachi HTS 543216L9A300
3. IDE1:
[COLOR="Red"]4. USB FDD:[/COLOR]
5. Network Boot: Atheros Boot Agent
6. USB HDD:



I'm guessing, but try changing the boot order so that the entry at position 4 is first in line. I think that is the flash drive.

Along the same lines, has the computer an option on start-up to enter the boot menu? You should see a message to that effect at some point, even if only for a very short time. Try that too. My laptop doesn't seem to take any notice of what set in the BIOS (yes, I know this is unlikely to be true). When I want to boot it from a USB stick, the only way is to select this boot menu thing and choose the (already plugged in) USB stick from there.

---

### Post by ThursdayNext on 2012-08-15
Worth a shot on FDD, but alas, no dice.
still trying to see if LS would give me anything at all, so I tried every permutation of

ls (hd0,1)/

and very exciting, it felt like something happened inside it, and it said
error: unknown filesystem
grub rescue>

which is still something different. I feel like the coma patient is occasionally twitching a toe.

---

### Post by unevenflow on 2012-08-15
Hey read this:
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

---

### Post by audiomick on 2012-08-15
Ok, have you looked at this?

[https://help.ubuntu.com/community/Grub2/Troubleshooting]("https://help.ubuntu.com/community/Grub2/Troubleshooting")

I don't think it is really going to help, though. There are references in there to Boot Repair, which I think is more or less what you need. 
What I think has happened is that your attempt to re-size the partitions has messed up the mechanism that tells grub, the boot loader, where the partition is that the system is on that it is supposed to boot from. Boot repair might be able to fix that, and the boot info script would at least give you good information about the state of things on the computer.
The problem is, you are not going to be able to get onto that until you can make the thing boot from the USB stick.

I'm going to have to bail out now, too. I hope someone useful sees this and responds, because I am not likely to  be back for 10 days or so, and probably can't really help much anyway. Hope some one else can.

---

### Post by ThursdayNext on 2012-08-15
> **unevenflow said:**
> Hey read this:
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)

> Find your existing Ubuntu partition and the module folder. 
Code:
ls                               # List the known drives (hdX) and partitions (hdX,Y)
ls (hdX,Y)/                      # List the contents of the partition's root
ls (hdX,Y)/boot/grub             # Normal location of the Grub 2 modules.
ls (hdX,Y)/usr/lib/grub/i386-pc  # Alternate location of the Grub 2 modules.
ls - should return all known drives (hdX) and partitions (hdX,Y)
ls (hdX,Y)/ - should show the contents of the root directory of the partition.
[COLOR="Red"]If you get an "error: unknown filesystem" this is not your Ubuntu partition[/COLOR]; more on that later.
If this is the Ubuntu partition, you will see the Ubuntu folders,...

Thanks. I've been going step by step and I get that error: "unknown filesystem"

And jesus, those directions are difficult and arcane, which I guess is how I've come to hate ubuntu. There are a lot of "ifs", and "return to sections" that depend on things happening that have not happened. I get <b>unknown filesystem</b> every time. It seems willing to set prefix, but what to set it to? When I followed the original set of directions to remove Ubuntu, I thought it was gone when I finished. So I reset the partition to be at 0 or near to it. Then on restart I got this grub nonsense. So it's looking for a partition that ubuntu's been removed from, and it's not looking on the usb stick at all as far as I can see, even though BIOS recognizes it.

---

### Post by ThursdayNext on 2012-08-15
> **audiomick said:**
> Ok, have you looked at this?

[https://help.ubuntu.com/community/Grub2/Troubleshooting]("https://help.ubuntu.com/community/Grub2/Troubleshooting")

I don't think it is really going to help, though. There are references in there to Boot Repair, which I think is more or less what you need. 
What I think has happened is that your attempt to re-size the partitions has messed up the mechanism that tells grub, the boot loader, where the partition is that the system is on that it is supposed to boot from. Boot repair might be able to fix that, and the boot info script would at least give you good information about the state of things on the computer.
The problem is, you are not going to be able to get onto that until you can make the thing boot from the USB stick.

I'm going to have to bail out now, too. I hope someone useful sees this and responds, because I am not likely to  be back for 10 days or so, and probably can't really help much anyway. Hope some one else can.

Thanks. What's funny is that I had removed Ubuntu before resizing!

---

### Post by audiomick on 2012-08-15
> **ThursdayNext said:**
> Thanks. What's funny is that I had removed Ubuntu before resizing!

Yes, but the boot loader, Grub2, is still there and still looking for the partition that has been removed. Or perhaps not finding the partition table it was expecting. I'm not that solid on that stuff.

This can all be fixed, but fixing it depends on getting the machine to boot from a USB stick. This is not related to the grub problems. Grub (or grub rescue) turns up after the machine has failed to realise it should be booting from the USB stick. Grub is on the MBR of the computer's hard drive.

[http://en.wikipedia.org/wiki/Master_boot_record]("http://en.wikipedia.org/wiki/Master_boot_record")

Grub is messed up, but if you are seeing that, it is because of another problem, i.e. the computer is not reacting to the instructions to boot from the USB stick. You need to concentrate on getting the boot from USB stick happening.

---

### Post by ads52 on 2012-08-15
> **ThursdayNext said:**
>  Rather than bother people in the threads, I messaged a couple of people who seemed to be on a lot and asked them for help, about a month ago. I haven't heard from them.

I know it is only a small part of your question but probably a large part of your disillusionment. Many people on these Forums will ignore PMs and prefer to answer queries in the open Forums, so do not take this as a sign of rejection of your queries :). This is an issue that has been addressed in an Ubuntu Forums FAQs post here:

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

See 'Don't' no. 9. So don't be disheartened by the failure of some to respond :).

---

### Post by slooksterpsv on 2012-08-15
You want USB HDD even if it's a flash drive. USB FDD is USB Floppy Disk Drive (rarely used) - so don't use that, move USB HDD at the top if you want to boot from a thumb drive or external hard drive.

---

### Post by audiomick on 2012-08-15
> **slooksterpsv said:**
> You want USB HDD even if it's a flash drive. USB FDD is USB Floppy Disk Drive (rarely used) 


Oops. You're right, of course.](*,)

---

### Post by ThursdayNext on 2012-08-15
> **ads52 said:**
> I know it is only a small part of your question but probably a large part of your disillusionment. Many people on these Forums will ignore PMs and prefer to answer queries in the open Forums, so do not take this as a sign of rejection of your queries :). This is an issue that has been addressed in an Ubuntu Forums FAQs post here:

[http://ubuntuforums.org/showthread.php?t=885580](http://ubuntuforums.org/showthread.php?t=885580)

See 'Don't' no. 9. So don't be disheartened by the failure of some to respond :).
Thanks---I was trying to not be at the bottom of stupid and waste people's public time if it was an easy fix. But that's good to know.


And as to FDD/HDD, I tried 'em both. The HDD sees USB HDD: Staples, and I got the usb from Staples, and apparently it calls itself staples. :o)
The usb feels pretty happy in itself, blinking away at me over there.
I've tried it and restarted in each of the three usb ports
it is the livestick I used originally to install ubuntu

is there a way at ls to force it to see the stick?


Hot dog! I tried another usb port and could see an external cdrom! I ran the repair disk for emachines and there was even a picture of an angel. Until the words "recovery failed" and then grub rescue>
but still--so I burned an iso from the same one I made the original stick from, and have booted up into ubuntu. 
I am at the "try ubuntu-netbook" "install ubuntu netbook" screen
and I realize I am terrified of doing more damage.
I can live with a teeny partition of ubuntu in the damn thing as long as I can still dual boot.

can I just install it? Will that fix the mess?

---

### Post by black veils on 2012-08-16
I didn't understand how you got it to boot, seemingly just from trying a different USB port. anyway, yes installing will make the computer work, if all you want on there is Ubuntu? or would you prefer Windows? or both?

don't use an old version of Ubuntu!  you need a recent one, get it from here [http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop")

if you have kernel problems, then install xubuntu instead [http://xubuntu.org/getxubuntu/]("http://xubuntu.org/getxubuntu/")
you want a "mirror" download of xubuntu. this operating system is also less resource hungry, yet with plenty of options. 

to create bootable flash drive:

verify downloaded file integrity -
Scroll down to "MD5SUM with Checksums
calculator"  [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")

create flash drive  [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/")

---

### Post by venky96 on 2012-08-16
Wait,Did you try using a different port? Maybe its a USB 3.0 port. Worth a shot,right?

EDIT: Oh wait you already did it. I guess the because the port was USB 3.0 .

---

### Post by mastablasta on 2012-08-16
seems there is an easy fix. either you repair grub using live Ubuntu boot repair utility: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
or you restore the MBR to windows only boot using windows fixmbr command or bootrec in windows 7. if you have windows 7 this is how you do it: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
 
 
otherwise i would backup and try again with latest edition 12.04 and newer kernel (=means also latest drivers). as suggested for netbooks maybe Xubuntu (but not necessary) might be a better choice. Another option is Kubuntu with netbook plasma desktop.
 
once you manage to install post here so people can help you troubleshoot the issue. instead of only searching on internet and then making a mess by using outdated guides and solutions.

---

### Post by audiomick on 2012-08-16
I would also suggest using the Boot Repair that Mastablasta linked to. That may well get the machine back to a state that you can boot from, and will deliver information about the state of the drive that will help decide what to do next.

---

