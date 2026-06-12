---
title: "Mounting preexisting RAID array."
date: 2013-09-25
forum: New to Ubuntu
---

### Post by LFGp3fK on 2013-09-25
Hi guys so yes I'm a Noob, but hopefully one that isn't too annoying, I do my research and I'm learning to be a developer ;) Just give me a gentle nudge if I say anything particularly stupid.

So I've managed to get ubuntu installed after getting around a hardware issue regarding a crappy Marvel SATA 3 controller, that's neither here nor there though. Here's the issue I'm faced with now. Actually 2 issues but I'll post about them one at a time till each if fixed.

I have a Windows 8 / Ubuntu 12.04. Dual boot config with a bunch of other hard drives. Here is how the hardware is organized:

120GB SSD - Windows 8 (Boot) <--- Grub installed here
750GB SSD - Ubuntu 12.04
2TB RAID 1 Array - 2x2TB physical drives
1TB extra HDD

Now I've got it so that Ubuntu and Windows boot fine from the Grub menu. However when I boot into Linux I see both physical HDDs of the RAID array as separate discs instead of a single array. I've done some research and realize that the Intel RAID "controller" is nothing more than "fakeRAID" in Linux and that I have to somehow enable software raid in linux for these drives. I've tried

sudo dmraid -ay

What I get is the following:

RAID set "isw_bggijbfdbd_The Warehouse" was not activated

So it's recognizing that there is a RAID array there but it's failing to activate it. How do I go about mounting / activating this RAID array in ubuntu? Note that I don't want to have to "activate" or mount the array every time I boot linux.

Thanks for any help. Learning things one bit at a time :D

EDIT: Oh and of course I don't want to wide the data on these drives, I just want to mount the existing array, if that makes sense.

---

### Post by newb85 on 2013-09-25
You might find the info here helpful: [https://help.ubuntu.com/10.04/serverguide/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/advanced-installation.html)

Obviously, you don't need to do this during installation, but it looks like the information still applies to GParted (which you'll have to install if you haven't already).

Disclaimer: I have no RAID experience.

---

### Post by LFGp3fK on 2013-09-25
Thanks for the resources newb85 but I solved the problem, well sort of lol. I found this very helpful resource that took me most of the way:

[http://kevinmccaughey.org/?p=182](http://kevinmccaughey.org/?p=182)

However I never quite managed to get it working that method. BUT one things he mentions there at the very beginning is that the volume label of the RAID array can't contain spaces. I had corrected this but for some reason Ubuntu refused to see the new volume label without the spaces and kept using the old one. I think that was one of the reasons that method didn't work. So I tried reinstalling Ubuntu and Boom with the new volume label with no spaces I didn't have to do ANYTHING at all, ubuntu automatically set up the RAID array, lol. So it turns out I didn't have to do anything but reinstall with the corrected volume label.

Thanks.

---

