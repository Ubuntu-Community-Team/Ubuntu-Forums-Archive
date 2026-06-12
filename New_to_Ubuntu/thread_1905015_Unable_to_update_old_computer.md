---
title: "Unable to update old computer"
date: 2012-01-05
forum: New to Ubuntu
---

### Post by Whamola on 2012-01-05
Hey everybody, so I recently got a computer of mine back from my family and am having problems with it.  It is running 9.04 and Update Manager says that it was last updated 897 days ago.  When I click "Check" everything fails to find anything. Clicking the "Upgrade" button to go to 9.10 tells me that I'm upgrading to a no longer supported version, then fails to fetch, saying that there may be a network problem.  I don't think that's the case since I was able to use firefox and install Folding@Home from the command line.

I tried "sudo apt-get update" and "sudo apt-get upgrade" and that also didn't work.  I also put in a cd which has 10.04.1 on it which it didn't boot from and didn't show up on the desktop.  Music cds also do not play, so that makes me think that there is a connection problem somewhere with them even though I opened the box and made sure everything was together before turning it on.

I don't see the option to boot from usb in the bios.

Does anyone have any ideas that I haven't tried to get this thing to update?  It's an old Gateway computer with a P3 (866MHz) if that helps.  I was going to use this mostly for folding@home and media storage, but I want to have it be up to date.

Thanks

---

### Post by sandyd on 2012-01-05
> **Whamola said:**
> Hey everybody, so I recently got a computer of mine back from my family and am having problems with it.  It is running 9.04 and Update Manager says that it was last updated 897 days ago.  When I click "Check" everything fails to find anything. Clicking the "Upgrade" button to go to 9.10 tells me that I'm upgrading to a no longer supported version, then fails to fetch, saying that there may be a network problem.  I don't think that's the case since I was able to use firefox and install Folding@Home from the command line.

I tried "sudo apt-get update" and "sudo apt-get upgrade" and that also didn't work.  I also put in a cd which has 10.04.1 on it which it didn't boot from and didn't show up on the desktop.  Music cds also do not play, so that makes me think that there is a connection problem somewhere with them even though I opened the box and made sure everything was together before turning it on.

I don't see the option to boot from usb in the bios.

Does anyone have any ideas that I haven't tried to get this thing to update?  It's an old Gateway computer with a P3 (866MHz) if that helps.  I was going to use this mostly for folding@home and media storage, but I want to have it be up to date.

Thanks
9.04 has reached EOL. Repos dropped.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

With the specs you posted, I would probably use Crunchbang

---

### Post by BertN45 on 2012-01-05
Both 9.04 and 9.10 have reached their End of Live. No updates nor upgrades anymore (Tried it on an old 9.04).

If you cannot install 10.04, that is still fully supported till 2013, you probably have a defect CD/DVD, since you also have the problem with audio CDs. That problem has nothing to do with the update issue on 9.04.

To be sure, try to see if you can read other CDs, if not the CD/DVD unit is defect and you will have to replace it. It is my experience that they are not very reliable, especially if you always push the door to close it. Get one from an old PC in some attic or buy one, they are not expensive. Besides the old ones from the 20-ties century are more reliable.

For the rest continue with 9.04 or install 10.04 LTS using a working CD unit. Looking at your hardware I would avoid Ubuntu 11.04 or 11.10 with the Unity desktop.

---

### Post by wildmanne39 on 2012-01-05
Hi, also lubuntu is light weight, just google to find a download site for it, there really is not much you can do with an out of date ubuntu.
Thanks

---

### Post by Whamola on 2012-01-06
So I found an old usb cd drive in my box of cords and misc computer parts, plugged it in, popped in 10.04.1 live cd and it showed up on the desktop!  It didn't pull up any sort of prompt which made me a little sad.  Can I trigger an update from the cd from the desktop?  Keep in mind that I have no way of rebooting from usb.

Thanks for dealing with my trouble.

---

### Post by Sigma1 on 2012-01-06
Rather than updating from the CD, which is possible, but risky, as updates are best done one step at a time, i.e. 9.04 > 9.10 > 10.04 etc., I recommend you boot from the CD and install from there. If you've got a bit of disk space, you could always consider installing 10.04 alongside 9.04, in case you're worried about the installation not going well (i.e. 9.04 system folders on one partition, 10.04 system folders on another and /home on a third). You don't say how old your machine is, but I'm running 11.10 ubuntu on a 2004 model, with a little added RAM. You only need to consider lubuntu, xubuntu etc. if you're really short of RAM.

---

### Post by drmrgd on 2012-01-06
If you can't boot from USB, and your CD / DVD drive is hosed, you might be stuck as I think you need to boot to an .iso image to proceed (I think you can't install an OS without unmounting the primary partition).  I could be wrong on this, though.  

I did do a quick search on alternate installs, and came up with this:

[https://help.ubuntu.com/community/Installation]("https://help.ubuntu.com/community/Installation")

If you scroll down to the section "Installation without a CD", there are a few other options depending on your setup. Maybe one of these would be relevant to your case?

Also, I think new DVD drives are fairly cheap.  So, it might be worthwhile to just get a new one and put it in if you plan on using this computer for a while.

---

### Post by BertN45 on 2012-01-08
Probably the easiest way is to put the CD of the USB drive in your PC. Half an hour of work and you only need a screw-driver.

---

### Post by Cheesemill on 2012-01-08
If the CD method doesn't work you can upgrade from 9.04 > 9.10 >10.04

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

