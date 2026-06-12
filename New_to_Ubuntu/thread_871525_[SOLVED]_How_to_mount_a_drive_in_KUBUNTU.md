---
title: "[SOLVED] How to mount a drive in KUBUNTU"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by ctoaun on 2008-07-27
I could not mount some drives (partitions) using the KUBUNTU "alternative install cd," so I created them with Gparted. How can I ensure that they will automount the same as my tmp partition or opt automount. Please, no f00 or whatever responses

---

### Post by boblemur on 2008-07-27
what you are looking for is /etc/fstab this is where you need to add a line for the partitions you need auto mounted and 
```

sudo fdisk -l 
```

will show you a list of partitions

---

### Post by ctoaun on 2008-07-27
I am  afraid to edit fstab because it looks too much like the registry in windows. Therefore, I saved a copy of it in documents. When people say edit fstab or add a line to fstab, they never specify where in fstab to edit or how to edit fstab, and I will not experiment with my fstab. Would you please clarify?

To anyone responding today, I'll probably not respond until tomorrow, thanks

---

### Post by DGortze380 on 2008-07-27
> **ctoaun said:**
> I am  afraid to edit fstab because it looks too much like the registry in windows. Therefore, I saved a copy of it in documents. When people say edit fstab or add a line to fstab, they never specify where in fstab to edit or how to edit fstab, and I will not experiment with my fstab. Would you please clarify?

use the command 
```

sudo gedit /etc/fstab

```

to edit fstab.

---

### Post by txcrackers on 2008-07-28
Using Kubuntu, you'd want to use
```
sudo kate /etc/fstab
```
when you're ready for it.

I would recommend starting your research, via the command-line (or via KHelpCenter) with "man fstab" - this is the Unix-style "manual" page for the /etc/fstab file. From there, it will probably lead you to "mount" (and so on). Use the entries already in there as a guide for what you want to do with your other partitions.

As long as you don't touch the existing entries, you can experiment fairly freely and expect your machine to keep functioning and be able to reboot without too much problem.

And it's **no where** as bad as the Windows registry. Once you understand the syntax, it's pretty simple. It's probably those UUIDs that make it look ugly... :D

---

### Post by DGortze380 on 2008-07-28
> **txcrackers said:**
> Using Kubuntu, you'd want to use
```
sudo kate /etc/fstab
```
when you're ready for it.




Sorry, forgot her was kubuntu.

---

### Post by ctoaun on 2008-09-24
> **DGortze380 said:**
> Sorry, forgot her was kubuntu.

The above instructions should work. The instructions below did work.

[COLOR="Red"]Solved:[/COLOR]
 [http://ubuntuforums.org/showthread.php?t=922445](http://ubuntuforums.org/showthread.php?t=922445)

**What one should note for Kubuntu is that Kate is used in lieu of gedit. This is of critical importance.**

Also, please note that with respect to LVMs, at least on my computer, there is a limit to the number of LVMs that the Kubuntu "alternative install" cd will allow one to make, and this limit is far lower than one would expect.
This means, at least in my experience, that even if one creates the partitions with Gparted, nothing no bash on or earth or in hell will mount them. I opened a bug report, but I've yet to receive a reply of any kind.

I hope this helps someone. To all of those above this reply, thanks

---

