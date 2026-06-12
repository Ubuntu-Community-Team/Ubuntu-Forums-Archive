---
title: "Installation"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by daniel136 on 2014-04-02
I've recently tried to install Ubuntu 13.10 on my laptop- the installation appeared to have completed successfully but now when I boot up I just get a black screen with a flashing underscore. It doesn't appear to allow text entry of any kind- but when I boot off the cd and go through the installation menu it tells me that it's already installed. Anyone know how I can proceed?

---

### Post by Double.J on 2014-04-02
Hi there!

looks to be that the system has installed fine, but the boot-loader hasn't been set up quite right.

first try running from the live cd in 'try ubuntu' mode. Pop open a terminal and try
```
 sudo fdisk -l
``` to double check your hdd has installed.

to fix grub (the program that loads ubuntu - also known as a boot loaded- at start up) see [here]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by steeldriver on 2014-04-02
I think it's more likely to be a graphics card / driver issue - can you get to a 'virtual terminal' by using the Ctrl-Alt-F2 key combo? Can you reboot into 'Recovery' mode by holding down the shift key during boot up?

---

### Post by daniel136 on 2014-04-03
Thanks for the advice. I tried the fdisk command and it looks as though the hdd is installed- I will also try fixing grub as suggested. Neither ctrl+alt+f2 nor shift gave me anything new :(

---

### Post by Double.J on 2014-04-03
Hi just another thought, but did you alter the boot options at the bios? If the hdd isn't in the boot list you can often get the flashing cursor on some systems?

if not when fixing grub, i'd recommend saving to the mbr of the disk ( /dev/sdx not /dev/sdx1 or /dev/sdx2, etc.)

---

### Post by daniel136 on 2014-04-06
Thanks everyone- problem solved!

---

