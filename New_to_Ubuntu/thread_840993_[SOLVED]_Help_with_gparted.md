---
title: "[SOLVED] Help with gparted"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by tstack77 on 2008-06-25
I have an old laptop with xp and hardy installed. The hard drive is only 20gb so space is at a premium for me (currently I have 10gb for each OS). I want to resize the xp space down to around 6gb and extend hardy's. The order on the drive is xp then hardy.

I fired up the live cd, opened gparted, and successfully resized the xp partition. My problem is with the extended partition in hardy. The 'Resize/Move' option is grayed out so I can't take advantage of the space I created in between the two.

Is this possible?

---

### Post by bluepowder7 on 2008-06-25
could it be limiting what you can do because it's an extended partition, and not a logical one?  you may need to "reconfigure" the hardy partition to be a logical one instead of extended before you can move it around.  best to back stuff up first!!!

---

### Post by tstack77 on 2008-06-26
I figured out that the swap space was mounted. I just unmounted it (swapoff) and am applying the changes now.

I didn't see any options to change extended to logical so I bit the bullet. I'll report back if it all works out (or not ;)

---

### Post by tstack77 on 2008-06-26
Success! Didn't even need to reinstall grub.

---

