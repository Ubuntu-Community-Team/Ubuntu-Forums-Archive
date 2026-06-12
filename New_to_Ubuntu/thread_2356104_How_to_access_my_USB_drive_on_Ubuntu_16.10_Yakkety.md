---
title: "How to access my USB drive on Ubuntu 16.10 Yakkety?"
date: 2017-03-20
forum: New to Ubuntu
---

### Post by soans on 2017-03-20
Any suggestions please on how to access my USB drive on Yakkety?  The print out when 'dmesg tail' is entered at the command prompt is in the attachment.
Appreciate any help.
John

---

### Post by Bucky Ball on 2017-03-20
Welcome. Plug it in and give us (copy/paste from terminal) the output of this:

```
lsusb
```

You'll probably see whether it's there or not. It obviously doesn't show in a file manager? Do you have Gparted or Disks installed? Open one of them and see of it shows up there.

What exactly are you looking for? This disk has partitions on it already or new, blank disk? If it's not picked up, is it plugged into a USB hub? If so, try plugging it directly into the computer and see if it's different.

PS: Just a word. Yakkety is an interim release which will be out of support in July at which time you'll need to upgrade the OS. If you have just started, you may prefer the latest LTS (long-term support) release, 16.04 LTS. This has five years support until 2021. LTS is generally good unless you have very new hardware which will only work with the newer kernel. Otherwise, the latest is not always the greatest. :)

---

