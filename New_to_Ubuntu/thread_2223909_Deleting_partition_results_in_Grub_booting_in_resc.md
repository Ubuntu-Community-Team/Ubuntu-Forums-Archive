---
title: "Deleting partition results in Grub booting in rescue mode"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by whitemarvin on 2014-05-13
Hello everyone, first time poster here.

I've been using Ubuntu 14.04 for the last two weeks, and It's been a smooth experience for the most part, until now.

Yesterday, I opened Ubuntu's Disks application and discovered that I had a 3 gb swap partition laying around that I didn't know existed. Given that I had no use for it, I decided to delete it, with the intention of adding the free space to another partition. Later, when I restarted my computer, instead of having the Grub boot menu show up, I was presented with the grub-rescue command prompt.

What happend? Is this a bug, or did I somehow manage to delete the bootloader? 
I've since reinstalled Ubuntu, as I had no idea what else to do, but I'm curious to know what caused this issue and whether it might happen again.

Thank you.

---

### Post by oldfred on 2014-05-13
System will boot without a swap, so just deleting swap would not cause system not to boot. And unless you had installed several times you would not have an extra swap.

If you did not mount partitions with UUID as is default, but changed to use device like /dev/sda1, perhaps partition numbers changed.

But now that you reinstalled everything is just speculation.

If you ran a BootInfo report from Boot-Repair at that time we could have seen exactly what the issue may have been.

---

### Post by whitemarvin on 2014-05-15
> **oldfred said:**
> If you did not mount partitions with UUID as is  default, but changed to use device like /dev/sda1, perhaps partition  numbers changed.

I had to read about UUID, as I didn't know what that was. My  installation was vanilla Ubuntu, and if Ubuntu  assigns UUID's automatically by default, then that shouldn't have been the cause.

> If you ran a BootInfo report from Boot-Repair at that time we  could have seen exactly what the issue may have been.

That's very useful to know, though I hope the problem won't repeat itself in the future. My thanks, regardless.

---

### Post by whitemarvin on 2014-05-16
The problem has occurred again. I extended my root partition using GParted, and now my computer fails to boot, and I encounter the following error:
"error: unknown filesystem.
Entering rescue mode..."

> **oldfred said:**
> If you ran a BootInfo report from Boot-Repair at  that time we could have seen exactly what the issue may have  been.
This time I came prepared: [http://paste.ubuntu.com/7474531/](http://paste.ubuntu.com/7474531/)

I would really appreciate the help.

---

### Post by Luke M on 2014-05-16
For some reason resizing the partition caused grub to not be able to find the linux partition. Reinstalling grub (with boot-repair) should fix the problem.

More details:
[http://www.gnu.org/software/grub/manual/html_node/GRUB-only-offers-a-rescue-shell.html](http://www.gnu.org/software/grub/manual/html_node/GRUB-only-offers-a-rescue-shell.html)

---

### Post by whitemarvin on 2014-05-16
> **Luke M said:**
> For some reason resizing the partition caused grub to not be able to find the linux partition. Reinstalling grub (with boot-repair) should fix the problem.

More details:
[http://www.gnu.org/software/grub/manual/html_node/GRUB-only-offers-a-rescue-shell.html](http://www.gnu.org/software/grub/manual/html_node/GRUB-only-offers-a-rescue-shell.html)

I clicked Recommended Repair in boot-repair, and I'm told: "FlexNet detected. Please backup your data before this operation. Do you want to continue?"

What do I do?

---

### Post by oldfred on 2014-05-16
Flexnet was an isssue but grub created a work around. So just go ahead and install.
Before flexnet & grub were both writing into sector 32 or there abouts.

       Adobe Photoshop, CAD/CAM, Rosetta Stone, Matlab others 
 see google search on others with same issue: flexnet site:ubuntuforums.org
Sector 32 is already in use by FlexNet
[http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2](http://www.amazon.com/Adobe-Photoshop-Extended-CS4-VERSION/product-reviews/B001EUDGO2)
The problem turned out to be Adobe's digital rights management software [DRM]. Do your own search for "FlexNet," formerly known as "SafeCast." What I have read is that FlexNet is a viral rootkit that replicates in multiple locations whenever a CS3 or CS4 product is installed, including trial versions.
Erase flexnet, if not using protected windows software anymore:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

---

### Post by Luke M on 2014-05-16
FlexNet is a copy protection scheme that writes into the same area as grub (space before first partition). I don't know what software is using it (or was using it...it could be a leftover from something you already uninstalled) and whether it's important to you.

Edit: Never mind, already answered above. (How do you delete a post?)

---

### Post by whitemarvin on 2014-05-16
That did it, Grub is working again.

Thanks a ton, guys!

---

