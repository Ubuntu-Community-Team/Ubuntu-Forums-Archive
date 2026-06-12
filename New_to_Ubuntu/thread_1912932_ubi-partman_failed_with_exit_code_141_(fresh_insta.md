---
title: "ubi-partman failed with exit code 141 (fresh install)"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by 118118 on 2012-01-21
i have tried wiping the live-usb and starting again and get the same error message.

i can skip this step but it says doing so may break the installation.

---

### Post by Double.J on 2012-01-21
Hi there, did you manage to resolve your issue?

I notice that a bug was filed about this issue in alpha builds of 10.04... trust this was resolved, but for those affected, the work around was to manually create the partitions to be used pre install using the gparted tool on the live usb?

Hope the issue has now been resolve/this helps?

All the best.

---

### Post by 118118 on 2012-01-22
11.10 xubuntu. i can only use this machone through a live-usb, and i'm not sure i understand your comment :popcorn:

---

### Post by 118118 on 2012-01-22
hi,

i reformatted the ubuntu parition, but now when i ask it not to install over the windows partition, i don't see an option to install on the "ubuntu" partition. it is set to automatically do so on the windows one...


halp!!


edit no it's not set to wipe windows but set to sda2 - which i just some "inexplicable" 4gb partition...

---

### Post by 118118 on 2012-01-22
hi,

managed to install ubuntu 11.10, was not an issue like with xubuntu. and have learnt a bit about partitions... not much :popcorn:!

may i please ask - is there any advantage to doing a fresh install via rebooting rather than thru the existing installation?
answer quick before i **** up something!

---

### Post by 118118 on 2012-01-22
hi, i made the fresh install now.


i have a few questions.

why did this happen in the first place [http://ubuntuforums.org/showthread.php?t=1912854](http://ubuntuforums.org/showthread.php?t=1912854) [http://ubuntuforums.org/showthread.php?t=1912881](http://ubuntuforums.org/showthread.php?t=1912881) ?
i made home and swap logical partitions - is that even vaguely right?

:popcorn:

edit oh yeah and now grub doesn't load............?

---

### Post by 118118 on 2012-02-26
> **118118 said:**
> i made home and swap logical partitions - is that even vaguely right?

:popcorn:

edit oh yeah and now grub doesn't load............?
i used fixparts to change the windows partition to symbolic, at least i think it was the windows partition. anyway grub still doesn't load, not even when i press shift even-though it says it will load grub when i do. i have tried editing grub settings to "saved" but when i set it to load 1 - the windows partition - the second partition in the list when i try fdisk -l, i get a bit of text then a option screen that i don't recognize flashes up and then i immediately get a blank screen and have to reset.

any help?

---

