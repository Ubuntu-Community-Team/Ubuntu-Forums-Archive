---
title: "No root system is defined"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by sundit1 on 2012-11-25
Thank you for answers to my previous post. I decided to download a free app from Paragon and successfully partitioned my HD, keeping Windows and intending to load Ubuntu 12.10 from bought disc onto the new partition.

When I click 'Install now' I get this message:
'No root system defined
Correct from partitioning menu'

Can someone please explain how to do this? I see no partitioning menu.

---

### Post by freedomAboveAll on 2012-11-25
Do you see something like an 'Advanced Install' option or something similar?  That goes to partition tool.

---

### Post by sundit1 on 2012-11-25
> **freedomAboveAll said:**
> Do you see something like an 'Advanced Install' option or something similar?  That goes to partition tool.
I don't think so but I will have to reboot Ubuntu to check.
Ok, now in Ubuntu. I get:

On 'Installation type' I click 'Something else'
I highlight the new (empty) partition '/dev/sda2 NTFS'
From 'Device for boot loader installation' I select  '/dev/sda2'
I click 'Change' and get a dialogue 'Edit partition'
It has a menu which defaults to 'Do not use partition'
  Other options on this list start with 'Ext4 journaling file system'
  and an option to format.

I don't know what I am doing with this. Is this where I should be?

---

### Post by sidzen on 2012-11-25
> **sundit1 said:**
>  . . .
On 'Installation type' I click 'Something else'
I highlight the new (empty) partition '/dev/sda2 NTFS'
From 'Device for boot loader installation' I select  '/dev/sda2'
I click 'Change' and get a dialogue 'Edit partitiion'"

[B]Use ext4
Mount point is / (root)
Choose a size (18-20GB)[/B]

It has a menu which defaults to 'Do not use partition'
  Other options on this list start with 'Ext4 journaling file system'
  and an option to format.

**Create New partition making sure no more than 4 exist on hdd***

I don't know what I am doing with this. Is this where I should be?

*Since / will be on /dev/sda2, it appears this is not a concern.

Now, create a /home partition using ext4 nd most if not all of the remaining space on the hdd

Continue with Install

---

### Post by Mark Phelps on 2012-11-25
You're encountering a problem because your formatted the new partition NTFS -- which is a Windows filesystem.  You need to Format that partition as Ext4 -- an option the installer is offering you.

---

### Post by sundit1 on 2012-11-25
Thank you folks, Ubuntu now installed and running.

A strange thing, though -
I partitioned as a last resort because although I originally wanted to install alongside WinXP, I was not given the option - until after I had partioned!
This seems like some alternative logic. I feel there must be an error in the system

---

