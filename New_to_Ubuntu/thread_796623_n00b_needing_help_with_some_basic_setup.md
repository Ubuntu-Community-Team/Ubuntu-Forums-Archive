---
title: "n00b needing help with some basic setup"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Rixii on 2008-05-16
I've asked for more explanation in other threads twice already, but apparently I'm an idiot who needs to be walked through step by step. I have a few things I need help with and will list them here. I have been using Ubuntu for a few weeks now and although I'm getting the hang of it, there's still some basics I don't get, so bear with me please.

My System:
Ubuntu 7.10 with kernel 2.6.22-14-generic (Only one OS on this system)
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
GeForce 8600 GT video card
SB Live! 5.1 sound card (with matching 5.1 speaker system)

*RESOLVED*I have the NVidia drivers installed, and my video card is running wonderfully, but I cannot select higher than 1024 x 768 resolution. Using the Sys Info program, I can enter the NVidia Display Settings and go to X Server Display Configuration. I find all the resolutions I could want but when I try to save it gives me this error message:
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

2) By looking through other threads and archived threads, I've managed to get my sound card working, and my on-board audio is turned off. However, I get sound only out of my front speakers, and I have no idea where to go from here. I gather this is a tricky card, so any help is greatly appreciated.

*RESOLVED* I still can't get my external hard drive (250 GB Seagate, almost full, formatted as NTFS) working. Can someone give me step by step instructions from the beginning? I have tried NTFS Config and other things but apparently I'm missing something. The drive works under Windows.

*SHOULD BE RESOLVED* When booting Ubuntu, I have to edit the kernel line to take out splash and add 'noapic' to get my system to load. Using the StartUp-Manager GUI, the splash isn't a problem anymore but I still have to manually add noapic at each boot. How do I do this permanently?

Thank you for any help.

---

### Post by robalcorn on 2008-05-16
> **Rixii said:**
> I've asked for more explanation in other threads twice already, but apparently I'm an idiot who needs to be walked through step by step. I have a few things I need help with and will list them here. I have been using Ubuntu for a few weeks now and although I'm getting the hang of it, there's still some basics I don't get, so bear with me please.

My System:
Ubuntu 7.10 with kernel 2.6.22-14-generic (Only one OS on this system)
AMD Athlon(tm) 64 X2 Dual Core Processor 5200+
GeForce 8600 GT video card
SB Live! 5.1 sound card (with matching 5.1 speaker system)

1) I have the NVidia drivers installed, and my video card is running wonderfully, but I cannot select higher than 1024 x 768 resolution. Using the Sys Info program, I can enter the NVidia Display Settings and go to X Server Display Configuration. I find all the resolutions I could want but when I try to save it gives me this error message:
Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

2) By looking through other threads and archived threads, I've managed to get my sound card working, and my on-board audio is turned off. However, I get sound only out of my front speakers, and I have no idea where to go from here. I gather this is a tricky card, so any help is greatly appreciated.

3) I still can't get my external hard drive (250 GB Seagate, almost full formatted as NTFS) working. Can someone give me step by step instructions from the beginning? I have tried NTFS Config and other things but apparently I'm missing something. The drive works under Windows.

4) When booting Ubuntu, I have to edit the kernel line to take out splash and add 'noapic' to get my system to load. Using the StartUp-Manager GUI, the splash isn't a problem anymore but I still have to manually add noapic at each boot. How do I do this permanently?

Thank you for any help.

in regards to your first problem you need to run nvidia-settings as root so open a terminal and run : sudo nvidia-settings this will save your selected resolutions.

---

### Post by Rixii on 2008-05-16
> **robalcorn said:**
> in regards to your first problem you need to run nvidia-settings as root so open a terminal and run : sudo nvidia-settings this will save your selected resolutions.

It works perfectly, thank you!

---

### Post by EXCiD3 on 2008-05-16
For problem #3, did you safely remove your NTFS drive from windows? sometimes if it isnt safely removed it will give you trouble mounting last time it was removed it will give you trouble mounting. It *should* automount in Hardy if it was safely removed last.

and for problem #4 just do a ```
sudo gedit /boot/grub/menu.lst
``` in terminal and add noapic to the line for booting Ubuntu that is displayed in the Grub menu when you boot.

---

### Post by ZabiGG on 2008-05-16
And since you asked for basic info, I also invite you to check out the links in my signature.

Have fun and welcome to the Ubuntu community ;)

---

### Post by Rixii on 2008-05-16
> **EXCiD3 said:**
> For problem #3, did you safely remove your NTFS drive from windows? sometimes if it isnt safely removed it will give you trouble mounting last time it was removed it will give you trouble mounting. It *should* automount in Hardy if it was safely removed last.

and for problem #4 just do a ```
sudo gedit /boot/grub/menu.lst
``` in terminal and add noapic to the line for booting Ubuntu that is displayed in the Grub menu when you boot.

My drive was safely removed from Windows, though occasionally the 'Safely Remove' button doesn't show up, in which case I would shut down the computer to remove it.

As for your next piece of advice, I had seen something like that before but couldn't get it to work. I was able to edit it easily this time however, so there should be no further problems, thank you!

@ZabiGG: I'm bookmarking that first link in your signature, it looks like a great thread to go through. I look forward to continuing with Ubuntu n_n

---

### Post by EXCiD3 on 2008-05-16
What do you mean by "almost fully formatted as NTFS"?

Shutting down the computer will also do a "safely remove" because for some reason Windows doesnt always display the icon in the taskbar. I've ran into the same problem. 

To try to manually mount the partition you can do this:

1) Create a directory for where you want it mounted (probably in /media)
```
sudo mkdir /media/External
```

2) If you dont know the drive location (/dev/hdXX) check fdisk:
```
sudo fdisk -l
```

3) Mount!
```
mount -t ntfs-3g /dev/sda2 /media/External
```

replace /dev/sda2 with the drive from the fdisk that shows up as NTFS. Make sure to include the number as otherwise it wont actually be trying to access the partition.

---

### Post by Rixii on 2008-05-16
> **EXCiD3 said:**
> What do you mean by "almost fully formatted as NTFS"?

Sorry, I mean that the drive is almost completely full and is formatted as NTFS. The only other drive I have with enough room to store that much data is the one Ubuntu is installed on, which is why I'd like to get mounted so I can transfer everything.

---

### Post by EXCiD3 on 2008-05-16
Ok, i just was wondering whether you had multiple partitions in different formats on it.

Trying to mount in the command line will show you the exact reasons your drive wont mount if it fails this way too.

---

### Post by Rixii on 2008-05-16
Alright, reading Kyral's intro to the terminal (Thanks ZabiGG!) means that I now have a good idea of what I'm doing.

@EXCiD3: When you talk about mounting from the terminal, what's the command for it? Am I going to be using the command to mount /media/usb ?

---

### Post by ZabiGG on 2008-05-16
you're quite welcome ;) When you want to thank someone who helped, you can click on the little medal icon located bottom right of their post.

Cheers ;)

---

### Post by EXCiD3 on 2008-05-16
> **Rixii said:**
> Alright, reading Kyral's intro to the terminal (Thanks ZabiGG!) means that I now have a good idea of what I'm doing.

@EXCiD3: When you talk about mounting from the terminal, what's the command for it? Am I going to be using the command to mount /media/usb ?
If you try mounting the drive in terminal and it fails, then it should give us an error and idea of what the problem is. The "mount" command is the one that does the mounting. The last parameter of the command, in the example i used /media/External, is the one that is the location the drive will be mounted to. Note that anything mounted into /media should show up in Places and your desktop (if you have desktop icons enabled).

---

### Post by Rixii on 2008-05-16
> **EXCiD3 said:**
> If you try mounting the drive in terminal and it fails, then it should give us an error and idea of what the problem is. The "mount" command is the one that does the mounting. The last parameter of the command, in the example i used /media/External, is the one that is the location the drive will be mounted to. Note that anything mounted into /media should show up in Places and your desktop (if you have desktop icons enabled).

Bah, when I looked at your reply earlier your example wasn't showing up? Maybe my brain fried.. Anyway, my drive does not show up in fdisk, and no longer shows up under the Sys Info program either even though it has previously. o_0 All that shows up is my internal hard drive and my two DVD/CD drives.

@ZabiGG: At least I know how to work forums, you've well received your thanks. ;)

---

### Post by ZabiGG on 2008-05-16
What can I say? ;)

Just trying to fulfill my Newbie Advocacy Mission :P

Sorry I stepped on your toes, tho. You just had very few posts, so my bad.

---

### Post by Rixii on 2008-05-16
> **ZabiGG said:**
> What can I say? ;)

Just trying to fulfill my Newbie Advocacy Mission :P

Sorry I stepped on your toes, tho. You just had very few posts, so my bad.

haha...well I'm sure there's plenty of people who wouldn't have known. I've been a computer/internet user for a long time now, just kept putting off my switch to Linux for the familiarity of Windows. I'm the one asking for help here, feel free to tell me anything you think I should know.

---

### Post by Rixii on 2008-05-16
So loading the drive on a separate WinXP system and safely removing it means the drive again shows up on my Ubuntu system. I've tried mounting it manually in the terminal as you showed me and it tells me only root can do that. After I add the sudo command, this is what I get:
> NTFS signature is missing.
Failed to mount 'dev/sdb1' : Invalid argument
The device '/dev/sdb1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Now, the drive was formatted by Windows XP, and has no partitions. All my files are accessible on a Windows system as of five minutes ago. What do I do from here?

---

### Post by Rixii on 2008-05-17
Can someone help me with where to go from here?

---

### Post by ZabiGG on 2008-05-17
I might be completely in the left field here, but maybe Super Disk Grub could help.

[Info here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").

---

### Post by Rixii on 2008-05-17
> **ZabiGG said:**
> I might be completely in the left field here, but maybe Super Disk Grub could help.

[Info here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html").

I'm not sure that's quite what I'm looking for. I can't boot my external, it's all data (video, music, pictures, programs)

---

### Post by meierfra. on 2008-05-17
Are you sure  that sdb1 is the correct partition? Post the output of

```
sudo fdisk -l
```
(l is a lower case L)

---

### Post by Rixii on 2008-05-17
> **meierfra. said:**
> Are you sure  that sdb1 is the correct partition? Post the output of

```
sudo fdisk -l
```
(l is a lower case L)

As sure as I can be, here's the output:

```
Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       89723   720699966   83  Linux
/dev/sda2           89724       91201    11872035    5  Extended
/dev/sda5           89724       91201    11872003+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08c8225c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30401   244196001    c  W95 FAT32 (LBA)

```

The 750 is my internal drive and the other two should be my DVD/CD drives. the 250 GB drive is my external

EDIT: Looking at it, it says FAT32? Is that right? I thought it was formatted NTFS but was I mistaken?

---

### Post by meierfra. on 2008-05-17
Yes, it seems to be  Fat32 partition. You can mount it via:

```
sudo mount -t vfat /dev/sdb1 /media/External
```

---

### Post by Rixii on 2008-05-17
> **meierfra. said:**
> Yes, it seems to be  Fat32 partition. You can mount it via:

```
sudo mount -t vfat /dev/sdb1 /media/External
```

Thank you! No wonder whatever I tried didn't work.. :oops: :lol:

With this, only my sound card is left. Can anyone help or should I try a more specialized forum?

---

### Post by EXCiD3 on 2008-05-17
Glad to see you got your external working finally :P Sorry i forgot to mention the different mounting options for fat32.

For your soundblaster card, you may want to try checking out this thread: [http://ubuntuforums.org/showthread.php?t=161817](http://ubuntuforums.org/showthread.php?t=161817)

---

### Post by Rixii on 2008-05-18
> **EXCiD3 said:**
> Glad to see you got your external working finally :P Sorry i forgot to mention the different mounting options for fat32.

For your soundblaster card, you may want to try checking out this thread: [http://ubuntuforums.org/showthread.php?t=161817](http://ubuntuforums.org/showthread.php?t=161817)

That thread completely confused me ^_^; And looking through the Comprehensive Sound Problems thread doesn't seem to talk specifically about getting a 5.1 system to work when only my front speakers are playing.

I think most of my confusion is because I don't understand enough about adjusting sound. I know the basics, and can even adjust settings in my sound in Windows, but that's because it provided explanations. I tried both alsamixergui and GNOME ALSA Mixer but I'm confused by all the settings there.

To be clear, the sound card is a SB Live! EMU10k1, and I have sound only from my front speakers; I'm trying to get the 5.1 system working.

---

### Post by EXCiD3 on 2008-05-18
Haha, okay. Lets start with your speaker setup and your soundcard. I've just got the standard 2 headphone jacks in my laptop but i have 5.1 simulated surround sound with my pc surround sound because of the matrix mode that i can enable on the speakers, so i dont really have much experience with the hardware end. How does the surround sound connect to your card? Does it have 3 cables, one for center, front and rear sound and inputs for each of these separately on your card?

---

### Post by EXCiD3 on 2008-05-18
:oops: <oops, wrong thread> :lolflag:

---

### Post by Rixii on 2008-05-18
> **EXCiD3 said:**
> Haha, okay. Lets start with your speaker setup and your soundcard. I've just got the standard 2 headphone jacks in my laptop but i have 5.1 simulated surround sound with my pc surround sound because of the matrix mode that i can enable on the speakers, so i dont really have much experience with the hardware end. How does the surround sound connect to your card? Does it have 3 cables, one for center, front and rear sound and inputs for each of these separately on your card?

Yes, it's pretty much how you describe it. The link below is my exact sound card. Brand new five years ago.:lolflag:

[http://reviews.digitaltrends.com/review/398/creative-labs-sb-live-5-1-review](http://reviews.digitaltrends.com/review/398/creative-labs-sb-live-5-1-review)

---

### Post by EXCiD3 on 2008-05-18
Actually now that i think about it, my parents comp that im using right now has a sb live card in it...its a dell they bought a while back that i use when im home from school. 

I just found this thread that should make it a lot easier for you to configure your sound card with, just make sure you log out after configuring it (Ctrl-Alt-Backspace): [http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147)

If my parents werent so picky id have Hardy installed on here and would probably have the same sound issue as you, but they wont seem to take the plunge no matter what i say...oh well, ill get them eventually! ;)

---

### Post by ZabiGG on 2008-05-18
Send them to my candid and engaging 101, Ex... they won't have a choice but to fold! rofl

Cheers,

Z.

---

### Post by EXCiD3 on 2008-05-18
> **ZabiGG said:**
> Send them to my candid and engaging 101, Ex... they won't have a choice but to fold! rofl

Cheers,

Z.

I might have to give that a shot :lolflag: The only success ive had so far is my dad uses ubuntu on his EeePC because 4gb for Windows and antivirus (which is like required for windows ;)) left 90mb free, and he wanted me to install Office 2007 on top of that...I installed ubuntu on that and now hes got 2gb free and enough software to last him for quite some time...but the family desktop of theirs i barely get to touch...i think they are worried id screw something up! yeah right, when has anything bad ever happened with a computer?!

---

### Post by Rixii on 2008-05-18
> **EXCiD3 said:**
> Actually now that i think about it, my parents comp that im using right now has a sb live card in it...its a dell they bought a while back that i use when im home from school. 

I just found this thread that should make it a lot easier for you to configure your sound card with, just make sure you log out after configuring it (Ctrl-Alt-Backspace): [http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147)

If my parents werent so picky id have Hardy installed on here and would probably have the same sound issue as you, but they wont seem to take the plunge no matter what i say...oh well, ill get them eventually! ;)

Actually you might not have the same problem, because I'm running 7.10 Gutsy. That utility looks really handy, but it didn't help. In the simple configuration mode, it detected my Live card, and told me to choose my speaker setup. After selecting 5.1, I put in a DVD but I'm still not getting the 5.1 sound. Under advanced configuration...well, I don't know what it means when it asks if I want to combine all sinks into one.

---

### Post by EXCiD3 on 2008-05-20
This might help for the sound issues if you use 8.04: [http://ubuntuforums.org/showthread.php?t=776739](http://ubuntuforums.org/showthread.php?t=776739)

---

### Post by whitethorn on 2008-05-20
Hi,

I have a Creative 24bit live USB card, spent a bunch of time getting it set up.  According to the ALSA webpage  

[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)

your card should be supported.  In a console type alsamixer and then go about turning up all the bars and once you've done that go into totem -> Edit -> Preferences -> Audio  and select 5.1 channel.  Reboot or restart X and see if that helped.  The best way to test if it works is by playing some song with totem, if you get playback on all the speakers than it's working.  

:)

---

### Post by Rixii on 2008-05-24
> **whitethorn said:**
> Hi,

I have a Creative 24bit live USB card, spent a bunch of time getting it set up.  According to the ALSA webpage  

[http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1](http://www.alsa-project.org/main/index.php/Matrix:Module-emu10k1)

your card should be supported.  In a console type alsamixer and then go about turning up all the bars and once you've done that go into totem -> Edit -> Preferences -> Audio  and select 5.1 channel.  Reboot or restart X and see if that helped.  The best way to test if it works is by playing some song with totem, if you get playback on all the speakers than it's working.  

:)

Alright, I've finally gotten around to trying it out (sorry I disappeared! >_<), but it's still not working. Using the GNOME ALSA Mixer, all the bars are set high enough where I should get sound. In Totem, I set it to 5.1 sound but I still don't get any sound from my back speakers.

That webpage you link does say it is supported, but it says I must turn on the sound support soundcore module and then gives me a command to see if it is already. When I enter "modinfo soundcore" this is what I get:
```
filename:       /lib/modules/2.6.22-14-generic/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22-14-generic SMP mod_unload 

```

---

