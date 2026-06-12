---
title: "Windows boot error, fix with Ubuntu?"
date: 2006-09-03
forum: Other OS Talk
---

### Post by acorn22 on 2006-09-03
I am dual booting from Windows XP to Dapper and I switch almost every day and today I could not boot up XP (Dapper is fine). I would get an error message in the middle of the splash screen that was only on the screen for about a half a second and then my computer would restart. I had to take a video of it, then put it on my mac, pause on that frame and take a screenshot of the video. I have attached the picture.

I was wondering if there is a way with Ubuntu to fix this missing file. (I think i can see the windows HDD with ubuntu, so mabye i could add the missing file on it?)

---

### Post by NetworkGuy on 2006-09-03
It looks like your Windows XP registry is corrupt.  I'm not sure if it can be fixed or not, but if it can be fixed, you'll need your XP CD to run the recovery console.

---

### Post by acorn22 on 2006-09-03
ok I do have my XP cd, so what do I do to restore my regestry?

---

### Post by phersotty on 2006-09-03
You could try booting from the XP cd and then choose fix or repair (I don't remember if those are the exact words) to get into the recovery console.  Then you could type fixmbr.   If you do this you will have to re install your boot loader because windows will write over it with its own boot loader.   Before you try anything though I would recommend backing up any important files in case something goes wrong.  You can backup your Windows files from inside Ubuntu by mounting the windows partition as you mentioned and then copying everything to a cd or usb drive depending on how your files are.

---

### Post by acorn22 on 2006-09-03
About the bootloader. 

I have GRUB installed on my Ubuntu hd, so it cant touch it, right? Then how do I delete the one Windows makes? Or will it be ok just to leave it there?

---

### Post by acorn22 on 2006-09-05
Ok, I tried booting from my XP cd and it wont boot. I tried booting from my Ubuntu cd without the windows drive in. For some reason my computer wont boot from cd. I checked the bios. Mabye the cd drive is bad :???:. 

At any rate, I can't boot from cd so could I somehow edit the regestry with Ubuntu? Is so, what would I edit? I'm sure someone here has done it before.

Also, I am not really sure how to mount the windows hard drive. At the moment I can't start my ubuntu either because it hangs at "Mounting root file system" so I cant experiment with it (but one it works I wont have much time to get windows running)

---

### Post by deanlinkous on 2006-09-06
Actually it looks like a hive dump. Here is one link
[http://www.kellys-korner-xp.com/xp_sys32.htm](http://www.kellys-korner-xp.com/xp_sys32.htm)
But I have never been able to recover from this cleanly at all. ](*,)

---

### Post by acorn22 on 2006-09-06
is there no way to use Ubuntu to copy over the file i need?

---

### Post by SoundMachine on 2006-09-06
> **acorn22 said:**
> is there no way to use Ubuntu to copy over the file i need?

Follow the advice in the link mentioned above. If that doesn't work.

The registry isn't a file you can just copy from somewhere, it's unique to your system.

Boot XP with the cd, choose repair installation, let it run, reboot, XP's bootloader will start XP, all programs will still be there, go to windows update and update everything, reboot and make sure everything is ok, put in the ubuntu-live cd, boot the system, chroot whatever directory the partition your previous install is mounted on and run sudo grub-install.

Just out of interest, have you been using any kind of "system optimizer" or "registry cleaner"?

---

### Post by phersotty on 2006-09-06
The only registry tweaking I have ever done was with regedit.  I'm not sure if you can just replace the file even if you could somehow locate it.  I don't think its a matter of just editing a simple text file like you can do with Linux and GRUB.  It does sound like a hive error as mentioned above.  It's also strange that you can't boot from CD even after editing the bios.  Sorry, I'm sort of out of ideas...

---

### Post by SoundMachine on 2006-09-06
Ahhh, i missed the part about your cd drive not working, is it working in Ubuntu though? What kind of system do you have? Does your POST screen tell you about any key to press to choose boot option, on mine, i press F2 and choose CD when i want to boot from CD, possibly removing the HDD from the boot list in BIOS will help?

If you need to do it through ubuntu you'll need the ability to write to an NTFS filesystem, there are guides on how to do that in the howto section. After that you do the following (I'll use /media/ntfs as the mountpoint in this example): 

# cd /media/ntfs/windows/system32/config
# mv software software.bak
# cp /windows/repair/software .

reboot

Now, the system will boot grub, choose windows and with any luck it should start. If not you will need a CD drive.

---

### Post by SoundMachine on 2006-09-06
> **phersotty said:**
> The only registry tweaking I have ever done was with regedit.

That is the most preferable way but also requires you to know what you are doing. Generally, the registry is better left alone, so are services and virtual memory management.

---

### Post by acorn22 on 2006-09-06
I can do some playing around to try to get my cd drive to work. I might see if the drive itself is bad.

I did use StyleXP once. And I used regedit to change my splash screen. But that was like a month ago.

And I used [this ]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")(only read ability, so I can't edit that hdd. Can I still some how edit even if I used that script?)

Oh, and here are my specs (Don't laugh)

Intel Mobo 
ATI Rage II C Pro
Assorted 150 Mb  RAM
Samsung (I think) CD RW
Intel PII 400 MHz (don't laugh)
6 GB HD - Linux
12 GB HD - Windows
WUSB54g v4 Wireless card (must be unplugged to boot system)
Microsoft USB laser mouse (Must also be unplugged)

So basically this box is a beater. I'm getting a new one soon i hope :) So dont wreak your brains over this.

---

### Post by phersotty on 2006-09-07
"So basically this box is a beater. I'm getting a new one soon i hope  So dont wreak your brains over this."

Well in that case format the drive and just make it a Ubuntu box !!  :-)

---

### Post by acorn22 on 2006-09-07
I wish life was that easy. See, I go to highschool online and one class I'm taking is Flash MX 2004. 

So you see my problem....

---

### Post by SoundMachine on 2006-09-07
> **acorn22 said:**
> I wish life was that easy. See, I go to highschool online and one class I'm taking is Flash MX 2004. 

So you see my problem....

If you'd like you can [donate]("http://www.taylorhorsepark.com/?L2=Taylor%20Horse%20Park&L3=Payment") some money (our family website) to help me buy my [new computer]("http://www.bestbuy.com/site/olspage.jsp?skuId=7869096&productCategoryId=pcmcat60700050016&type=product&tab=1&id=1149040473547") quicker. (grand total is $330)

Check if you can get the CD ROM drive working, if you can, PM me and i'll walk you through it.

No donation from me though, the money i have to donate goes to OpenBSD which are hurting because companies like Canonical, RedHat and Novell like to use their software without giving them a cent when they now need it.

---

### Post by acorn22 on 2006-09-07
I was only half serious about the donations. (Do donate if you can :D :D )

There must have been an off setting in my bios cuz I just hit "restore defaults" and now it boots!

The only problem is that I boot up the disk (XP) and it tells me to press f2 to begin the ASR (automated system recovery) so I do. Now it tells me I need to insert some floppy disk. To make the floppy disk they tell me to go into my control panel.... Wait a minute! I can't even boot! Doh!

So, If someone would be kind enough to make the disk, ([Directions here]("http://kb.iu.edu/data/aorb.html")) copy it's contents, and email them to me (only 1.4 MB) at acorn22 gmail com that would be great. 

Hey, at least then YOU'LL be ready with the disk!

---

### Post by SoundMachine on 2006-09-07
> **acorn22 said:**
> I was only half serious about the donations. (Do donate if you can :D :D )

There must have been an off setting in my bios cuz I just hit "restore defaults" and now it boots!

The only problem is that I boot up the disk (XP) and it tells me to press f2 to begin the ASR (automated system recovery) so I do. Now it tells me I need to insert some floppy disk. To make the floppy disk they tell me to go into my control panel.... Wait a minute! I can't even boot! Doh!

So, If someone would be kind enough to make the disk, ([Directions here]("http://kb.iu.edu/data/aorb.html")) copy it's contents, and email them to me (only 1.4 MB) at acorn22 gmail com that would be great. 

Hey, at least then YOU'LL be ready with the disk!

You don't want to do this, the ASR will erase everything, what you want is to use your original XP cd or a copy of the same version and do a reinstallation, boot from the disk and hit r and that is it.

It doesn't matter if you download it from a torrent or whatever, as long as it's the same version as you got with your computer it's a-ok legal.

Besides, no one can make that (floppy) disk for you, it needs to be made from your computer.

---

### Post by acorn22 on 2006-09-07
ooh ok.

And, my computer never gives me the option to press R. I'll try anyways.

You hit the nail on the head. I downloaded XP for my class (I regret it) and the disk came with [one of these automated installers]("http://uwininstaller.tk").

---

### Post by acorn22 on 2006-09-07
Oh, and another reason (the main one) that I can't just re-install windows is because it has all my music on it. 

So If someone could point me to a good step by step guide to connecting to an OS X computer (I'm on it now) from Ubuntu, I could unload all the music onto this mac and then be fine to delete everything.

Besides I wanted to swtich which drives linux and windows where on anyways.

---

### Post by SoundMachine on 2006-09-07
> **acorn22 said:**
> Oh, and another reason (the main one) that I can't just re-install windows is because it has all my music on it. 

So If someone could point me to a good step by step guide to connecting to an OS X computer (I'm on it now) from Ubuntu, I could unload all the music onto this mac and then be fine to delete everything.

Besides I wanted to swtich which drives linux and windows where on anyways.

If it's not legal, you will need a licence, if you are in school, you can get that for about $10 and you will get a cd with it.

If you had a legal version, you could have called someone by now and had it fixed by now. The advantages outweigh the cost in the long run which is why so many choose to pay. ;)

Personally, I just can't justify software piracy when it's not needed and so i say goodbye and i hope it works out for you. :)

BTW, Samba rocks. ;)

---

### Post by acorn22 on 2006-09-07
If what's not legal? Moving my music?

---

### Post by SoundMachine on 2006-09-09
> **acorn22 said:**
> If what's not legal? Moving my music?

Why would you even ask that?

Your copy of WinXP of course, you do realize you have free support by calling them?

---

