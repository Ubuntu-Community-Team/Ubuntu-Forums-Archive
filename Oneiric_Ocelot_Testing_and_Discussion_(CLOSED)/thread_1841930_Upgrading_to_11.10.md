---
title: "Upgrading to 11.10"
date: 2011-09-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Kodeine on 2011-09-10
Salutations!

So I tried to update to the beta release of 11.10. But three times now whilst update manager is in the process of downloading packages it freezes and starts using lots of CPU. Now update manager has 418mb of new packages it says it wants to download. It also asks if I want to run a partial upgrade (probably due to it freezing before).

How can I remove these new packages from update manager and stay on 11.04?

Thanks bye!

---

### Post by howefield on 2011-09-10
Thread moved to #*Ubuntu +1 (Oneiric Ocelot)*"

---

### Post by Kodeine on 2011-09-10
Okay so this is what my desktop looked like [http://i.imgur.com/oZ5ln.png](http://i.imgur.com/oZ5ln.png) I tried to update to 11.10 once again and this time it did not freeze. I was able to use nautilus and see my desktop wallpaper towards the end of the update. So everything was seemingly coming back together.

But after restarting this is what I get now. This happens when I try recovery mode or normal boot on the new kernel. [http://imageshack.us/photo/my-images/30/dscf2538k.jpg](http://imageshack.us/photo/my-images/30/dscf2538k.jpg)

***Turns out I can boot into a older kernel. Can't remember which one it is but it's the one at the very bottom of the list. Good news. When I do unity is being used. Well at least I've got that now (Hal-a-ula). What can I do to fix this mess?

---

### Post by cariboo on 2011-09-10
> **Kodeine said:**
> Okay so this is what my desktop looked like [http://i.imgur.com/oZ5ln.png](http://i.imgur.com/oZ5ln.png) I tried to update to 11.10 once again and this time it did not freeze. I was able to use nautilus and see my desktop wallpaper towards the end of the update. So everything was seemingly coming back together.

But after restarting this is what I get now. This happens when I try recovery mode or normal boot on the new kernel. [http://imageshack.us/photo/my-images/30/dscf2538k.jpg](http://imageshack.us/photo/my-images/30/dscf2538k.jpg)

***Turns out I can boot into a older kernel. Can't remember which one it is but it's the one at the very bottom of the list. Good news. When I do unity is being used. Well at least I've got that now (Hal-a-ula). What can I do to fix this mess?

Truthfully, you shouldn't be doing an upgrade yet, but seeing as you have, have you started in recovery mode and selected dpkg from the menu. This should update your system and install any missing packages.

---

### Post by Kodeine on 2011-09-10
> **cariboo907 said:**
> Truthfully, you shouldn't be doing an upgrade yet, but seeing as you have, have you started in recovery mode and selected dpkg from the menu. This should update your system and install any missing packages.

Using which kernel? I Remember trying recovery mode with the new kernel but thats when i got the error in the imageshack link. Havent tried recovery mode with any other kernel i think. I'll try again later and report back my findings.

---

### Post by cariboo on 2011-09-11
Recovery mode doesn't start X, so use the current kernel.

---

### Post by effenberg0x0 on 2011-09-11
This happens when grub is messed up. You have a kernel update without a grub update or with an interrupted grub update. The other option would be if you had compiled your own kernel with no support for your filesystem, which I believe you did not.

If you can get to a console with networking, either in recovery or normal mode, you could try:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install --reinstall linux-image-generic
sudo reboot now

I believe grub will find the available images, recreate the menu entries with the correct options and update initram, the way it is supposed to. It should be ok after a reboot.

If you cannot get to a console, it is possible to do this using a Live CD/USB if you have one available, but the procedure is a little different (you have to mount the root partition and chroot into it, etc...)

Regards,
Effenberg

Ubuntu Oneiric is Beta 1. It is expected to not work 100% and is not what I would personally recommend for anyone that just needs to get the job done. It's aimed at beta testers and people that can afford to have a broken PC right now. So PLEASE: DO NOT attempt any of the mentioned procedures if you're working on a server / production machine, if you don't have backup of your data or if you don't have the habit of performing fixes in Ubuntu / Linux distros. You can end up having to do a new install from scratch. I can't be held responsible for any damage, ok? :-)

---

### Post by Kodeine on 2011-09-11
I backed all my stuff up and are currently putting it back on a clean 10.10 installation. Probably best if I stay clear of beta releases. I wonder why it froze when I first tried to update to 11.10? Ow well I'm glad to see my desktop again.

---

### Post by cariboo on 2011-09-11
@Kodeine, If you want to try out Oneiric, why no use gparted to free up some hard drive space, and install Oneiric on it's own partition.

---

