---
title: "Resizing Partition with Gparted"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by iSuck on 2008-07-21
Hello

Everything I'll be explaining requires you to look at the attached image.

----------------------
Xubuntu 8.04
Laptop:
HP Pavilion dv6458se
AMD Turion 64X2
NVIDIA GeForce GO 6150
----------------------

I'm having many problems with linux (even with different distros) on this laptop, so I decided to take it off and only have it on my desktop. I've been messing with it for 3 months and it's just irritating. I'm not blaming Linux, but I'm blaming HP for putting sh**ty hardware on this laptop

If you look at the picture, on the Gparted window, on the lower box, I formatted the ext3 (xubuntu) already. Then I extended the fat32 (Personal and media files) to fill up the space the ext3 has left behind.

Now my real question, there are:
[LIST]
[*]/dev/sda1 "extended"
[*]/dev/sda5 "ntfs"
[/LIST]
Both containing Windows XP, I suppose. I want to resize the windows partition smaller and resize the fat32 to fill up the empty space again, but which of the two on the list above do I resize? I want to make sure I do this correctly.

This may not be a ubuntu question, but I'm using the LIVE CD to use Gparted.

Please help. Many thanks in advance.

Sinc
TN

---

### Post by Tim Sharitt on 2008-07-21
I think you will have to resize /dev/sda5 to where you want it and then resize sda1 to match. sda5 is a logical partition within sda1.

---

### Post by logos34 on 2008-07-21
> **tim sharitt said:**
> i think you will have to resize /dev/sda5 to where you want it and then resize sda1 to match. Sda5 is a logical partition within sda1.
+1

---

### Post by iSuck on 2008-07-22
What's up with the +1?

Thanks!

---

### Post by bumanie on 2008-07-22
As far as I know, one has to resize the logical partition before being able to resize anything within it. Also as vista is inside the logical partition, vista may not boot - windows generally (there are a few exceptions) has difficulty booting from any partition that is not a primary partition, preferably on the first partition of a hard drive. Having vista inside sda1, will likely cause problems.

---

### Post by logos34 on 2008-07-22
> **iSuck said:**
> What's up with the +1?

Thanks!

i.e. 'I agree'

---

