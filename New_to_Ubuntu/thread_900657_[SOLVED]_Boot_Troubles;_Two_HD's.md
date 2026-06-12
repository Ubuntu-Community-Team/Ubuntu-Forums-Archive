---
title: "[SOLVED] Boot Troubles; Two HD's"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by RevTom on 2008-08-25
Hi,

I have a Windows XP system with two hard drives.  I used GParted LiveCD to do a quick format of my smaller HD, and then installed ubuntu on it.  Everything seemed to go fine with the installation.

However, I can't get to ubuntu at all.  My computer automatically loads windows.  There seems to be no way to choose ubuntu instead.  Certainly I have no option at boot up.

I tried a fix I saw on these forums.  You are supposed to open a terminal window.  I used my GParted LiveCD to boot and then used the terminal app from the main screen.   I was then supposed to type: "sudo grub"  and then a few other things.  Typing "sudo grub" got me an error messages, so that got me nowhere.

Anyone got any thoughts for me.  Somewhere, Linux is waiting for me on my system.  I just can't get there.

---

### Post by zamadatix on 2008-08-25
if you installed ubuntu after xp grub sholdve been install properly. could you tell us the error messages that came up?

---

### Post by RevTom on 2008-08-25
That's the thing -- there is no error message, no nothing.  My computer simply boots straight into Windows XP.  There is no screen available to choose boot options, or anything like that.  In fact, I haven't been able to get into my BIOS since installing Ubuntu, either.

And yes, Ubuntu was installed after XP.

Thanks...

---

### Post by bobnutfield on 2008-08-25
It appears as though Grub is not installed at all.  It would usually have been installed to the MBR of your first hard drive to give you the boot options.  If you have the live Ubuntu CD (not the Gparted CD), run it and go to a desktop and open a terminal and type:

> sudo fdisk -l

and post the results.  From there, we can help you to install grub and create the correct entries to get Ubuntu and Windows booting correctly.

---

### Post by RevTom on 2008-08-25
> **bobnutfield said:**
> 
If you have the live Ubuntu CD (not the Gparted CD), run it..

I assume you mean my installation CD?  Or is this some other form?

---

### Post by bobnutfield on 2008-08-25
Did you install from a Live CD (a full Ubuntu Desktop from a live cd)?  Or, did you use the alternate install cd?  If you used the alternate cd, you can still install grub, but it is a little more complicated than with the live cd.

---

### Post by SuperSonic4 on 2008-08-25
Yeah, he means the installation CD. Pick the option that says "try ubuntu..." at the top

---

### Post by kansasnoob on 2008-08-25
This is troubling:

> I haven't been able to get into my BIOS since installing Ubuntu, either.

Can you still boot into the Ubuntu Live CD?

I've never not been able to go to BIOS on boot if I pushed my "delete" key. Of course this varies depending on MOBO manufacturers, but that's troubling.

---

### Post by zamadatix on 2008-08-25
well if you scroll to the top of the list i ment when you typed sud grub in the live gparted cd what messages came up.

---

### Post by partsdale on 2008-08-25
"Typing "sudo grub" got me an error messages, so that got me nowhere."

I believe this is the error message that he was referring to.

---

### Post by zamadatix on 2008-08-25
thats what i ment, what did those error messages say? (might tell why grub isnt working)

---

### Post by bobnutfield on 2008-08-25
When you are able to open a desktop with a live cd, this is the instructions you need:

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/")

---

### Post by RevTom on 2008-08-25
Ahh, now we may be on to something.  I used a CD given to me by friend, which has "alternate" written on it.  Maybe somehow GRUB never got loaded.  

Another possiblity is that I loaded grub onto my secondary HD, which is where I installed ubuntu.  But it would have to be on the primary HD (the first boot HD after the CD) for GRUB to work, wouldn't it?
I think I can use the alternate CD to put GRUB on the primary HD, but it makes me slightly nervous.  Will partitioning it (which, it seems, I must do) wipe out any of my data in windows?  And if not, when I resize the paritition, how do I know which part will contain windows, and which the boot loader?

I just now finished my own download of Ubuntu, and I'll burn the ISO to a CD in a sec.  If I go that route, will I have to somehow "uninstall" what I've done already?

---

### Post by alzie on 2008-08-25
The live cd will format the second drive before it installs so there won't be anything to uninstall.

The only thing that bothers me is if you rebooted with the alternate cd in the cd drive it still should have given you a menu to install Ubuntu.

At any rate, burn the iso at a slow rate (4x is often recommended) and hopefully this will get you going again.

---

### Post by RevTom on 2008-08-25
Well, the Live CD is certainly more user friendly.  The ultimate result was no different however -- still boots directly into Windows, with no options for alternative boots along the way.  

At least now with the live CD I can get into Ubuntu and open a terminal and try out some of the other stuff.  I'll do and post again.

Does anyone have any thoughts on the following:
Could my problem be that I installed Ubuntu on the second HD, while the BIOS is keyed to boot from the first HD?  In other words, is it possible that GRUB is installed -- just on my secondary HD.  If that is the problem, then
a) How do I put it on the first HD
b)Can I do that without corrupting Data on the first HD?

---

### Post by alzie on 2008-08-25
I'm dual booting with 2 hard drives.  Due to my own fault I decided to reinstall my Ubuntu on the second drive<edit Yesterday>.  Win XP pro uses the first.

I had no issues with the reinstall,  I gave the second drive entirely to Ubuntu and grub still took over from MBR.

I can't understand unless your computer has some sort of write protection for the MBR to prevent unauthorized access?

Anyway assuming you have hd1 as master and 2 as slave I can't see any reason for this not to be working.

Maybe posting your computer specs will give some help.

---

### Post by RevTom on 2008-08-25
Well,

I WILL mark this problem as solved.  Apparently I had some goofy BIOS settings.  First, I have too many many machines, and forgot the key to enter bios (it was a funky one, like f2).  Next I just went through and reverted most of my BIOS settings to default.  Then when I went to boot -- voila, the boot manager was there, and I could choose my options.

Thanks to ALL of you for your replies and suggestions.

---

