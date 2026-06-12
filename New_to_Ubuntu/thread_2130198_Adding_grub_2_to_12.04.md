---
title: "Adding grub 2 to 12.04"
date: 2013-03-28
forum: New to Ubuntu
---

### Post by phil66 on 2013-03-28
I now have 10.04 on sda1 with grub-1.98 to mbr
I installed 12.04 to sda3 and update -grub to add it to grub menu

Since 10.04 is near eol I want to delete it
How do I install grub to 12.04 mbr

Do I do this before or after deleting 10.04

---

### Post by kc1di on 2013-03-28
Hi phil66.

I would go[ here]("https://help.ubuntu.com/community/Boot-Repair") and download and run boot-repair  it will install grub2 to the mbr for you.
you can do it before or after you delete 10.04. good luck :)

---

### Post by oldfred on 2013-03-28
Boot-Repair is always a good choice to have to make repairs and know how to use.

But if dual booting and you can boot into 12.04, you can just install grub to the MBR.
Boot into 12.04 and run this if your drive is sda.
       sudo grub-install /dev/sda

You can also run this which is like the original install.
      
 sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

