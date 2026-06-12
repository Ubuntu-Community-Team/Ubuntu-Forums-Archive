---
title: "[SOLVED] Grub Menu"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by adobrakic on 2008-06-18
I just realized you can edit the Grub menu, and i was wondering if it's necessary to have all those Ubuntu versions on the menu? I wanted to delete all of them except the latest one, and just leave windows along with it.

bad idea?

---

### Post by NikoC on 2008-06-18
Well what you usually read on these forums is to keep two versions of Ubuntu, i.e. the previous one and the last one. Just in case something goes wrong you can always boot into another 'version'.

You can remove the older ones via synaptic (linux kernel) and when you do they should be gone from Grub as well.

Hope this helps you out.

Cheers.

---

### Post by adobrakic on 2008-06-18
thanks for the heads up, ill try this out. :D

---

### Post by Dedoimedo on 2008-06-18
Hello,

First, ALWAYS backup the existing menu before making any changes:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup

Now, if you want to make changes, do it, just keep consistent and make sure you don't remove entries that you need to boot the different operating systems / distros.

BTW, what are all those versions that you refer to?

Dedoimedo

---

### Post by adobrakic on 2008-06-18
I'm not really sure what they're called, but you know how there's a couple versions of ubuntu, and then any other OS you got on there? I have v.16 - .19 (dont exactly know the way the numbers are arranged)

Also, i looked up "linux kernal" under synaptic, and couldn't find anything.


--edit--
If anyone else wants to do this, look up "Linux Header" in synaptic, instead of "Linux Kernal"

---

### Post by iaculallad on 2008-06-18
First thing for you to do is edit your /boot/grub/menu.lst file:

-Create a backup first, just in case:

> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.original

-Open file for editing:

> gksu gedit /boot/grub/menu.lst

-You can then delete/comment out the "unwanted" boot options. Save and close file.

Secondly, go through Synaptics and use "linux-image" (w/o quote) to search for old/unused kernels and try to remove them.

---

### Post by coolaj86 on 2008-06-18
You can edit menu.lst so howmany=2 and that means only 2 kernels will be displayed - the most recent and one backup.

---

