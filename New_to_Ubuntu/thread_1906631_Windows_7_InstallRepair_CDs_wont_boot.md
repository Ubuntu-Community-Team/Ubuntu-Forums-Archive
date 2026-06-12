---
title: "Windows 7 Install/Repair CDs wont boot"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by DrDRD613 on 2012-01-09
Just as the title says.  I'm trying to reinstall Win7 after wiping the old windows off it, now I need to go back to Windows for my school program.  Problem is, when I try to boot from either the repairCD, installCD, or recovery partition, Ubuntu automatically loads up no matter what, with no options given.  It's like the CD's aren't even there.

---

### Post by mikewhatever on 2012-01-09
Make sure the BIOS is set to boot from the CD, that's what governs the boot order priority.

---

### Post by Double.J on 2012-01-09
> **mikewhatever said:**
> Make sure the BIOS is set to boot from the CD, that's what governs the boot order priority.
+1 if you left the recovery partition intact on your device it may still be in your grub menu also.

Let us know how it turns out :) Just remember that when you re-install windows, it's bootloader will knock grub 2's entry out of the mbr - so it'll just load up windows straight away. you'll either need to use your ubuntu live cd to change this, or the [super grub disk]("http://www.supergrubdisk.org/")

Best of luck.. don't get too taken in by windows ;)

---

### Post by DrDRD613 on 2012-01-09
> **mikewhatever said:**
> Make sure the BIOS is set to boot from the CD, that's what governs the boot order priority.

I've gone to the bios options before startup and set boot order so that the CD is first, still with the same result.

---

### Post by Double.J on 2012-01-09
> **DrDRD613 said:**
> I've gone to the bios options before startup and set boot order so that the CD is first, still with the same result.

Are you using an external dvd drive? these can often only be booted from if you resart, not a cold power on? Can the DVD's be read by ubuntu?

---

### Post by DrDRD613 on 2012-01-09
> **gnu/mirow said:**
> Are you using an external dvd drive? these can often only be booted from if you resart, not a cold power on? Can the DVD's be read by ubuntu?

No, it's the built-in drive for the laptop.  
I'm using DVD-R data discs, would using a different type of disc such as CD-R work better?

---

### Post by Double.J on 2012-01-09
The laptop would have to be pretty old not to boot dvd-r's and the windows installer won't fit on a cd surely? you say neither disk will boot up? can an ubuntu live cd? this could eliminate the dvd/cd issue, the integrity of the disks or a hardware issue. I have previously been able to get windows 7 installer on a usb stick, but the program I had to use only ran on a windows machine.

---

### Post by DrDRD613 on 2012-01-09
I've been able to run the Ubuntu Live CD no problem, it's just the Windows DVD's that wont run.  I can open the DVD and see the .iso I burned onto it, so there seems to be no problem with the drive itself.

---

### Post by QIII on 2012-01-09
You have eliminated other bootable media and the drive itself as sources of failure.  Try another disk, to be sure.  Maybe an older Live CD.  If that works, your recovery media itself is suspect.

---

### Post by Stamos on 2012-01-09
> **DrDRD613 said:**
> Just as the title says.  I'm trying to reinstall Win7 after wiping the old windows off it, now I need to go back to Windows for my school program.  Problem is, when I try to boot from either the repairCD, installCD, or recovery partition, Ubuntu automatically loads up no matter what, with no options given.  It's like the CD's aren't even there.

How'd you wipe windows off your computer? I can't even sign on to mine anymore and it's just useless space!

---

### Post by Double.J on 2012-01-09
> **Stamos said:**
> How'd you wipe windows off your computer? I can't even sign on to mine anymore and it's just useless space!

Do you really want to remove windows, I'd be inclined to reinstall it or repair it - it can be useful for things not supported in wine such as full outlook support, games and bios flashing?

Of course if you really aren't going to repair it, it's dead space and should probably go (did you use ubuntu to get anything off it you wanted?) you'd do this from the live cd - after you've backed everything up! 

use the program gparted, delete windows partitions (these would be ntfs partition(s) at the far left of the display - check it is the windows partition! right click, delete, click apply.

You could then either install another distro in the space, or reclaim your space by extending ubuntu to the left - this will take a long time and you must have backed up first.

once that's done, run these command in the terminal

```

mkdir /fix [COLOR="Green"]name doesnt matter[/COLOR]
mount /dev/sda[COLOR="Red"]X[/COLOR] /fix [COLOR="red"]X is the number of the ubuntu partition as shown in gparted[/COLOR]
mount -o bind /dev /fix/dev 
mount -o bind /proc /fix/proc 
chroot /fix bash 
sudo update-grub 

```
then reboot

if your not sure of anything ask :)

---

### Post by satanselbow on 2012-01-09
> **DrDRD613 said:**
> I can open the DVD and see the .iso I burned onto it

If you can "see" a file called something**.iso** then you will never boot that particular disk.

You need to use the "Burn Image" function of your disk burning app.

In K3B (for example) this is under Tools->Burn Image.

You cannot just burn an ISO file as data - it needs special handling as above ;)

---

### Post by Double.J on 2012-01-09
> **satanselbow said:**
> If you can "see" a file called something**.iso** then you will never boot that particular disk.

You need to use the "Burn Image" function of your disk burning app.

In K3B (for example) this is under Tools->Burn Image.

You cannot just burn an ISO file as data - it needs special handling as above ;)

Good spot satanelbow! (and username!) really didn't spot that first time around - wood for the trees! 

The default burner is brasero - copy your iso to the dektop, stick a blank disk in and right click> burn with breasero.

Can't remember if it gives you the option of burn speed - if it does, choose the slowest. Any problems with brasero, as satanselbow says install k3b or similar :)

---

