---
title: "A couple questions regarding &quot;safely ejecting&quot; from USB ports"
date: 2015-08-30
forum: New to Ubuntu
---

### Post by elvis6 on 2015-08-30
When I have a flash drive plugged into my USB port, and I want to safely eject it, and right-click on it, I get 2 options. 1) Eject 2) Safely remove.
What exactly is the difference between the 2 ? 
Are they the same, or is the "Eject" option not actually "safe" since it doesn't say so, like option 2 ?

My other question is, when I want to safely eject a Wireless Adaptor, I cannot find an option to do so.
I only find the option for safe eject when I have Flash Drives or thumb drives plugged in, and not Wireless Adaptors.
Or should I not be concerned ? Does this mean that there's no chance of damaging a Wireless Adaptor, just by pulling it straight out ?
I'm wondering, because with other operating systems I've used, even the Wireless Adaptor has the option for "safe eject"

---

### Post by Dennis N on 2015-08-30
Eject and Safely Remove: Two Ask Ubuntu explanations and discussions:

[http://askubuntu.com/questions/5845/what-is-the-difference-between-unmount-eject-safely-remove-drive-and-the](http://askubuntu.com/questions/5845/what-is-the-difference-between-unmount-eject-safely-remove-drive-and-the)

[http://askubuntu.com/questions/86019/what-is-the-difference-between-eject-and-safely-remove-device](http://askubuntu.com/questions/86019/what-is-the-difference-between-eject-and-safely-remove-device)

My Xubuntu system doesn't show Safely Remove for USB flash drives. Only Eject and Unmount. 
My Ubuntu system has all the options.

Other usb devices aren't mounted to the file system and you can just unplug them without worry. Includes keyboard, mouse, controllers, microphones, and your wireless adapter.

---

### Post by SeijiSensei on 2015-08-30
Drives need to be cleanly unmounted before removal so that any open files will be closed first.  Otherwise you can lose data.  As Dennis says, that doesn't apply to other USB devices.

That same logic applies to any physical drives in the machine.  You'll notice that if you simply turn off the power to the machine, Ubuntu will run a file system check the next time you turn it on.  There's no guarantee in these situations that files that were in use when the power was turned off will still be intact.

---

### Post by The Cog on 2015-08-31
Just closing any open files is not enough to be sure youcan unplug the drive. You may notice that sometimes it takes a long time (up to 20 seconds?) to say it's safe to remove the drive. During this time, the system is busily writing out any changes that are still held in the disk cache in memory. This just goes to show how much data you might lose if you just pull a drive, and interrupting that flow can leave the filesystem corrupted.

There are times when you can see a difference between unmount and eject. If a USB stick is formatted with multiple partitions (e.g. a FAT partition and a btrfs partition) then generally, both of these get auto-mounted when the stick is inserted. Each partition can be unmounted separately, but ejecting one partition makes the other partition unmount as well. I don't know if the other partition is correctly flushed first or not.

I have also seen in some versions of Ubuntu (not recently) that eject also makes the light on the USB stick go out - I wonder if it is switching off the 5v power.

---

