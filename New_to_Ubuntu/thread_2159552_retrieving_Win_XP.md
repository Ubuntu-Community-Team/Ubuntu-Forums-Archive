---
title: "retrieving Win XP"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by Rolandl on 2013-07-03
Ubuntu 12.10 issues:  
 
Hi. I am new to Linux and having difficulties.
 
 I partitioned hard disk and installed Ubuntu 12.10 alongside my Windows XP. Am able to use Ubuntu, which is slow to load, but now I cannot boot my XP. It is not in the boot menu. I downloaded and burnt the xp iso. Image file to disk but this won't boot either. Apparently the partitioning was correct.

 Roland

---

### Post by sudheesh001 on 2013-07-03
Hi Rolandl,

This looks like a GRUB issue. You can repair it by booting a Ubuntu Live CD and using 'Boot Repair'

Here is what you could do

If you have an Internet connection you can just insert your Ubuntu CD  (the one you used for installing ubuntu 12.04) and select "Try Ubuntu".  It will then boot a live environment of Ubuntu from the CD.

1. Once the live environment loads, open Terminal.
2. Then type in the following commands after the $ sign.

[FONT=courier new]sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[/FONT]
followed by

  [FONT=courier new]sudo apt-get install -y boot-repair && boot-repair[/FONT]

After that launch Boot-Repair and select "Recommended Repair".  That should fix the problem.

For furthur detailed help have a look [here]("https://help.ubuntu.com/community/Boot-Repair")

Enjoy. :)

---

### Post by Impavidus on 2013-07-04
If it doesn't work, show us the boot info summary. It will help us find out wat is wrong on your system.

---

### Post by slickymaster on 2013-07-04
> **sudheesh001 said:**
> Hi Rolandl,

This looks like a GRUB issue. You can repair it by booting a Ubuntu Live CD and using 'Boot Repair'

Here is what you could do

If you have an Internet connection you can just insert your Ubuntu CD  (the one you used for installing ubuntu 12.04) and select "Try Ubuntu".  It will then boot a live environment of Ubuntu from the CD.

1. Once the live environment loads, open Terminal.
2. Then type in the following commands after the $ sign.

[FONT=courier new]sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update[/FONT]
followed by

  [FONT=courier new]sudo apt-get install -y boot-repair && boot-repair[/FONT]

After that launch Boot-Repair and select "Recommended Repair".  That should fix the problem.

For furthur detailed help have a look [here]("https://help.ubuntu.com/community/Boot-Repair")

Enjoy. :)

+1
[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
It's a simple tool to repair frequent boot issues, like when you can't boot Ubuntu after installing Windows or another Linux distribution, or when you can't boot Windows after installing Ubuntu, or when GRUB is not displayed anymore, some upgrade breaks GRUB, etc.

---

