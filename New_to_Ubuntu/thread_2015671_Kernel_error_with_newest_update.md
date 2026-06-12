---
title: "Kernel error with newest update"
date: 2012-07-03
forum: New to Ubuntu
---

### Post by BlackWolfe on 2012-07-03
After updating Ubuntu (I have it installed on a WD Passport USB Drive) it now pull up with an error stating that "I need to load the kernel first".  Complete newb when it comes to Linux/Unix so I don't know any of the mechanisms of how Ubuntu works, or how to "load the kernel" myself. Apologies if this has been addressed elsewhere here but I couldn't find this particular problem.  When it gives me a list of versions I run (am running) the previous version of Ubuntu (sorry about the non # info) and it works alright except for some keyboard-quit-working issues. 

Any and all help is greatly appreciated.

---

### Post by Redblade20XX on 2012-07-03
Does this occur as the system boots? As in after the BIOS screen you get this message.

-Red

---

### Post by msammels on 2012-07-03
What version of Ubuntu are you running? Also - have you tried using:

```
sudo apt-get update
```

To make sure everything is up to date? If this occurs during system boot, like Redblade20XX asked, it could be a corrupt install.

---

### Post by matt_symes on 2012-07-03
Hi

This sounds like GRUB may be looking for the kernel but cannot find it. Check GRUB. 

I'm off to bed though so i cannot help till tomorrow. I'm sure others will help you though like the two posters above.

Kind regards

---

### Post by sandyd on 2012-07-03
> **BlackWolfe said:**
> After updating Ubuntu (I have it installed on a WD Passport USB Drive) it now pull up with an error stating that "I need to load the kernel first".  Complete newb when it comes to Linux/Unix so I don't know any of the mechanisms of how Ubuntu works, or how to "load the kernel" myself. Apologies if this has been addressed elsewhere here but I couldn't find this particular problem.  When it gives me a list of versions I run (am running) the previous version of Ubuntu (sorry about the non # info) and it works alright except for some keyboard-quit-working issues. 

Any and all help is greatly appreciated.
Try running
```

sudo update-grub
```
and try it again.

---

### Post by BlackWolfe on 2012-07-03
Really appreciate the replies. 
@RedBlade20XX - Yes, it's after the BIOS comes and goes, and right after the "Orange Box" appears on my monitor.

Running the stuff suggested. We'll see what happens. And the corrupt install sounds like it would fit the bill.

Thanks again.

---

### Post by msammels on 2012-07-03
If updating GRUB fails, I would redownload the ISO, check the MD5 sum and just nuke the partition, assuming you haven't got much to loose (this is why I have /home on a separate drive (not partition)).

Hey, here's an idea... if updating GRUB fails, I can also suggest something like this:

```
sudo apt-get dist-update
```

Which will update everything the distro came with. I remember I used to have trouble with LiveCDs by burning them too fast, but since I've switched to USB, the problem has vanished. Anyway, sorry, I'm just rambling now. Try updating GRUB, and a dist-update, and if it fails, unless someone else here is technically savvy with GRUB, I would recommend a reinstall.

---

### Post by BlackWolfe on 2012-07-04
I appreciate everyone's help on this. I tried the grub update suggestion, but then when it rebooted it took me to a screen that looked like a terminal screen with this:

grub:


I tried to get a list of help commands but the list was too long and I have no idea how to get it to halt (I know DOS backwards and forwards, Linux/Unix? Not so much). So I downloaded a new ISO on another computer, burned it, and it 'said' that I could install it (I'm using a WD My Passport for this) 'along side' the old installation, and thought "Hey that way I can get to all my files and transfer them." 
Nope. Won't work at all now. So, I'm going to do a clean install and that should work I would imagine. Losing some bookmarks is no big deal (I managed to snatch my pictures off before it went off on me) and the rest of my files will just have to be a loss. And now I'll make sure to back-up everything I don't want to lose before updating anything. ;)

Again, you all RAWK! Thanks for your help! :guitar:

---

### Post by BlackWolfe on 2012-07-05
Now it seems there's a new problem. I tried to do a fresh install of Ubuntu 12.04 LTS, the version that this whole thread began with. For some reason it would not format the WD My Passport that I've been using for Ubuntu (from the start) so that I could do the fresh install. So I moved the Passport to another computer, erased all the partitions and let it do a windows XP format on the drive, which is what was there when I first installed Ubuntu (I think it was vs.9? 10?) a while back. Then I brought it back to this computer and had it do a clean install of 12.04 LTS. Same problem. So I repeated the cleaning the HD steps and then installed this current version 11.10 onto the HD. Rebooting got me this:

error: file not found
grub rescue: (blinking cursor)

The above occurs after the BIOS has gone through it's motions (as it does whenever I'm using a Windows XP drive say) as if everything is fine. I've checked the boot order to make sure that it is correct. 

I have to be honest about this I have NO CLUE what grub is, or how to access it (I do know how do open the terminal however) and/or fix it. From the beginning, all my installs have been from ISO burn CDs, and I have done the installation from the boot-up menus, not from the desktop install icon. 

Since I can access the internet from the Live CD (either version works fine that way) I'll give anything you can recommend a try. I just want to be able to boot to the Passport HD and save my files there like I did before. 

IF THIS HELPS: All of this trouble started when I let Ubuntu upgrade from 11.10 to 12.04. After THAT reboot is when everything went FUBAR.

I appreciate all the help you can give a rookie. Thanks ahead of time!

---

