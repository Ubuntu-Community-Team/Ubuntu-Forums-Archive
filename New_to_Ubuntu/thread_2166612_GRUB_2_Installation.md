---
title: "GRUB 2 Installation"
date: 2013-08-10
forum: New to Ubuntu
---

### Post by sydney2 on 2013-08-10
Hi there
How Do I manually install  GRUB 2 and configure it to boot a Ubuntu partition

Please Help.......

Sydney..

---

### Post by grahammechanical on 2013-08-10
Please give us more information. Describe the situation or the problem. What hardware do you have? What version of Ubuntu do you have? Is there another operating system installed as well as Ubuntu? Are you able to load Ubuntu? Are you able to load the other operating system?

Without answers to these kind of questions you may get advice that is not appropriate for your situation.

Regards.

---

### Post by sydney2 on 2013-08-10
Well I'm sorry and should have actually described by problem. Well here is the problem I faced.I had Installed Ubuntu 12.04 LTS Desktop. Instead of using the automatic Dual Boot Option I installed it to a custom partition I created (using palimpsest) made for it.Similarly installing the GRUB 2 boot loader to the same partition where Ubuntu was to be installed in spite of using the default option. Another partition contained  Windows XP installed to it. I then restarted as prompted but it would just boot to XP and no signs of the GNU GRUB Menu and neither Ubuntu.As per my knowledge I feel Grub was not installed properly or not at all.So I shall I recover from the problem?

Any help would be greatly appreciated..........

Thanks a million

Sydney............

---

### Post by Bashing-om on 2013-08-10
sydney2; Hi ! 

Let me nudge things along a bit... You have defined the problem ... now show us what we are working with and on ;
Terminal codes (key combo ctl+alt+t yields a terminal):
```

sudo fdisk -lu 
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
"Assuming" you have but one physical hard drive installed.
Expect it to be straight forward to install "grub" properly where bios can find it.

[INDENT][INDENT]ain't noth'n but a thing
[/INDENT][/INDENT]

---

