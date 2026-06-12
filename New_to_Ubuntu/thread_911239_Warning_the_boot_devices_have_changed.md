---
title: "Warning: the boot devices have changed"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by 2CV67 on 2008-09-05
Hi community!

I am dual booting Hardy with XP via grub (I think..).

I have a USB hard drive for backup purposes, which I attach for backups then usually but not always remove to a different location for safety, so it is frequently on & off.

Whenever I have added or removed it & then boot up, the boot process stops before the grub screen, with the message:
> Warning: the boot devices have been changed.
BBS boot priority will be affected. Please enter setup to check

I then need to press F1 to continue booting.
This is a nuisance, especially if some other family member is trying to boot - I don't want the kids dealing with this kind of stuff - they have been told to stop if they get warnings!

Of course, I am not arguing that the devices have been changed, but is this warning normal?
Can I avoid it or disable it?

Thanks!

---

### Post by Pro-reason on 2008-09-05
This isn't an operating-system thing.  Ubuntu is simply reporting what the motherboard is telling it.

You need to enter the BIOS configuration when you switch the machine on (you usually have to press Del or F12), and change the boot settings.

---

### Post by 2CV67 on 2008-09-06
Thanks, Pro-reason (& I do agree with your signature!).

Yes, I understand that there really has been a change in the boot devices.

I just wonder if everybody with a USB drive has to put up with this warning every time they add/remove?

And:
> You need to enter the BIOS configuration when you switch the machine on (you usually have to press Del or F12), and change the boot settings.
You mean I have to go through that every time I add/remove the USB drive?
Or can I make some once-&-for-all change to the settings which will allow booting from the normal HD whether the USB drive is there or not?

For the moment, I just F1 to continue booting after the warning, without changing anything.

Thanks for any clarification!

---

### Post by Pro-reason on 2008-09-06
> **2CV67 said:**
> 

You mean I have to go through that every time I add/remove the USB drive?
No, if you had to do that, it would be simpler to just make sure it's not plugged in at boot time!

I mean that there are probably settings that determine how USB devices are treated.  You need IDE and SATA hard drives to be prioritised over all USB devices.  Since I'm not familiar with your motherboard, I can't be more specific.

It's also possible that you need to remove the “boot” flag from the external drive.  You can set such flags using the *GParted* application.

---

### Post by 2CV67 on 2008-09-06
Thanks for your patience...so far!

I checked with GParted & the USB drive does not have a boot flag - just a lba flag for the fat32 partition.
The main HD has one boot flag (& lba flag) for the fat32 (XP) partition.

I attach pictures of the BIOS pages in case they provide any clue.
I don't see anything too crazy...

---

### Post by unutbu on 2008-09-06
This may or may not help, but out of curiosity,
when you say you "add and remove" the USB hard drive, what do you mean exactly? 

When you plug in the USB HD, is it automounting, or are you typing a mount command? 

Before you unplug the USB HD, are you right-clicking the hard drive icon and selecting "unmount", or are you typing a umount command?

If you are only doing these things, it is not normal for your BIOS to think the boot priority has changed. If you are doing anything other than the above, that might be interesting to know.

---

### Post by 2CV67 on 2008-09-06
Thanks Unutbu.

What I usually do & works just fine is:
1. Boot first & then hot-plug the USB drive - it is then autodetected/mounted in either Ubuntu or XP & works OK with no action from me.
2. Shut down the PC after that session & then cold-unplug the USB drive.
The next boot is then OK.


Another method which does work is:
1. Hot plug as above. (OK)
2. Unmount in Ubuntu or use "safe withdrawal" method in XP then disconnect USB drive before shutting down PC.
Next boot OK.

What I often do & does not work is:
1. Hot plug as above. (OK)
2. Shut down the PC after that session but don't unplug the USB drive.
The next boot is then NG (warning...F1).
If I still leave the USB drive connected, subsequent boots are OK.
But if I then disconnect by any method, the next boot is NG (I think...).

Also NG is:
1. Cold plug the USB then start PC.
That boot is NG.

Hope that is clear(ish).....

How do real men do it? ;)

---

### Post by unutbu on 2008-09-06
What happens if you
[list]
[*]Disable "Silent Boot". 
[*]Disable "Boot Other Device"
[/list]
in the BIOS menu?

---

### Post by 2CV67 on 2008-09-06
Thanks, but...
No effect on the problem.

I get to see an extra screen at the start of every boot now, but still get the warning & need to F1 every time I boot with/without the USB drive different from the previous boot.

:confused:

---

### Post by egalvan on 2008-09-06
Do you use the USB device to actaully BOOT from?

If this IS a bootable device, then I'll need to study on it some more.
No help at this time.

If NOT, then remove the USB from the list of BOOT DEVICES in that second BIOS screen.

The BIOS may be getting upset that the BOOT DEVICE ORDER is changing. This may, or may not, help. I've had motherboards react in both ways.

(actually, removing non-bootable devices from the boot order is a good idea in general. It speeds boot processes, and can give a small measure of security against bad bood devices (floppy, etc,)

ErnestG

:popcorn:

---

### Post by 2CV67 on 2008-09-06
Thanks for your suggestion!

No, I do not use the USB device for boot.

I went to the second screen, but could only find options for changing the order of the 3 devices, no way to remove one...
Sorry but I am not familiar with that area (yet!).

Could you say how to remove it please?

---

### Post by 2CV67 on 2008-09-09
The USB device in the second screen is there/not-there depending on whether the actual device is connected/not-connected.

I don't see any way of over-riding that automatic action...

Any further suggestions please?

Thanks!

---

### Post by Pro-reason on 2008-09-09
All motherboards are different, so we can't know without seeing that screen.  You just have to look through the options yourself and see what can be changed.

---

### Post by gldearman on 2008-09-09
I happen to have this same BIOS, so maybe I can help.
[I]
But I am wrong[/I] <original post deleted, since it doesn't solve the problem>

I tried changing the **Boot Other Device** setting to [Disabled]. No good.  I think that the issue is that in Hard Drive Boot Priority settings, USB Flash memory is listed as a hard drive.  You can lower its priority, but you can't remove it from the list. If you want to boot from the hard drive, you have to allow the BIOS to try booting from the USB.

You may be stuck with this.  I've been stuck with it for 2.5 years.  It no longer really bothers me -- just remember to pull out your USB drive after powering down.

You could try the motherboard manufacturer, and see if they have any technical support -- but I doubt it.  There was no website or even phone number listed in the manual for my motherboard.

Sorry I couldn't help.

---

### Post by 2CV67 on 2008-09-10
Thanks very much for trying, anyway! :)

Sure this is not a major problem & I can easily live with it.

I just have a principle of trying to fix problems whenever I can, especially if the anwer is quite simple once you know (which it nearly always is once somebody shows me!).

Fixing one problem often helps when you get to the next problem.

This is how I am slowly getting my Ubuntu towards where I want it.

I guess this one is not really an Ubuntu problem anyway...

Thanks guys!

---

