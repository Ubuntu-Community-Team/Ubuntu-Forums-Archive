---
title: "Ill-advised Gimp removal attempt, now unbootable, save a few files?"
date: 2019-10-17
forum: New to Ubuntu
---

### Post by nginmu on 2019-10-17
I did an admittedly stupid thing last night.

Working on the basis that the best way to learn is to try things & accept the inevitable mistakes, for some odd reason I took it into my head that I wanted to update Gimp. Why I thought Gimp needed updating I don't know. I think a bottle of cider had something to do with it.

I decided to select the main Gimp entry in Synaptic for complete removal. As far as I can recall this then prompted the system to tell me about other related packages that needed some sort of attention. In a nutshell I think I ended up selecting a fairly large number of what looked to me like Gimp-related packages, plus a few more that maybe didn't look all that Gimp-related just from the names but which the system seemed to be telling me wanted removal.

Applying the changes, I sat and watched the terminal process many many lines. A lot of terminal lines warned me about dependency problems, but went on to say "removing anyway, as you requested"

After all this had completed, I received a few messages about having to fix broken packages before discovering virtually nothing seemed to work, most desktop links had no target, etc.

Tried a reboot but the system stalled very early on in the boot sequence.

The only thing I have on this laptop that I'd like to recover if possible is the Thunderbird profile folder. Apart from that, it's no problem to just wipe everything & start over with a new install.

I have, apart from the lubuntu laptop I've broken, a windows 7 laptop with SATA HDD. The broken laptop is quite old & it's hard disk is an IDE type.

I'm vaguely thinking of remedies involving a lubuntu live CD, or maybe repartitioning the disk and installing a fresh lubuntu on part of it, such that I might then be able to use the new installation to access the 'other side'..?

I guess I could try repairing the existing damaged installation but I wouldn't be too sure where to start. The terminal did seem to be delving nastily deep when it was removing things :-(

Any good ideas as to what's the best approach to rescuing the Thunderbird profile files appreciated

---

### Post by Impavidus on 2019-10-17
My only rule about alcohol and computers is: After drinking alcohol, don't do anything that requires root permissions.

You can access your home directory with your thunderbird profile (and everything else on your hard drive) using the live disk. That's the same one you use for the fresh install. Just boot the live disk, select "Try before installing", copy the stuff to want to keep to a usb drive, unmount and unplug the usb drive. Then make a fresh install and restore your backups.

---

### Post by nginmu on 2019-10-17
Worked a treat. Had a hiccup or 2 because of permissions, managed to use chown -R on the .thunderbird user directory to gain sufficient priveliges to get it all off onto a USB stick. Thanks for pointing me in the right direction.

---

