---
title: "Ubuntu 12.10 only loads in recovery mode"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by professorgraham on 2013-02-10
I am new to Ubuntu. I am running dual boot (OSX, Linux) on a  Macbook i7 2.3 GHz Intel Core i7. Graphics card is Intel HD Graphics  4000 384 MB/NVIDIA GeForce GT 650M. I am using rEFTIt as my bootloader. 

**My issue** is that I  can only access Ubuntu 12.10 through recovery mode. When trying to  load directly from the bootloader, I never get passed the purple  screen, sometimes a black screen with blinking cursor key.

Any ideas why this might be happening? I have read that it may be an issue with the graphics card, but I am not sure. Any step-by-step guides on how to resolve this issue would be greatly appreciated!

Thanks you!

---

### Post by 1Norris on 2013-02-10
How do you get into recovery mode please?

---

### Post by professorgraham on 2013-02-10
Via Grub. Second menu option. I have since fixed this problem by following these instructions from terminal in Ubuntu: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Seems to hang in relation to my (switchable) video card!

---

### Post by grahammechanical on 2013-02-10
So, you are getting to a Ubuntu desktop using Recovery mode (Resume?). Open System Settings>Software Sources>Additonal Drivers tab and change video drivers. There are several there that you can experiment with. I have found Nvidia drivers to be problematic over the last few months.

Does this Macbook have Nvidia Optimus technolgy? If so you need a specialist video driver. Nvidia do not provide one at the moment. Look here:

[http://bumblebee-project.org/]("http://bumblebee-project.org/")

If Ubuntu was working fine, then try an older kernel.

Regards.

---

### Post by professorgraham on 2013-02-10
Yep. Installed bumblebee. Now working nicely. Thanks.

---

