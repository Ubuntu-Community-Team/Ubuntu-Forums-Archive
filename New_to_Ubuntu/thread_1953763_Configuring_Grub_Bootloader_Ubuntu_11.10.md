---
title: "Configuring Grub Bootloader Ubuntu 11.10"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by oneforthetruth on 2012-04-06
Hello, new to the forum! 

I have a few partitions on my 300gb hard drive of varying sizes. My operating systems right now are Ubuntu 11.10, Backtrack 5 R2 (just to fiddle around with) and then a data partition. My bootloader menu is getting a little crowded, and since Backtrack is Ubuntu, the menu is full of Ubuntus and I'd like to clean it up a bit. 

What is the most efficient way of editing these menu options? And out of curiosity, what cool things can I do with my bootloader menu? Thanks!

---

### Post by garyed on 2012-04-06
The best solution I've found is to make my own 40_custom menu.
40_custom is a file in /etc/grub.d/ 
There's a lot of good info out there on making a 40_custom file in grub2.
You can copy & paste all the menuentry items you want from /boot/grub.cfg into the 40_custom file & even change the menu names to your liking. Then run update-grub.
Once you get all the entries you want you can make some of the other files in /etc/grub.d unexecuteable so you can have a totally customized menu.

---

### Post by garvinrick4 on 2012-04-06
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by oneforthetruth on 2012-04-06
Thank you! That is very helpful

---

### Post by bodhi.zazen on 2012-04-06
IMO easiest way of cleaning up your menu is to remove old kernels.

You can do this from synaptic or Add/Remove software.

IMO you do not need more the 2 - current kernel + one old working kernel.

Then update grub.

---

### Post by garvinrick4 on 2012-04-06
Open a terminal and copy and paste this will give you kernels installed then open Synaptic and can
type in search window by kernel number and can remove from there as stated in previous post. Enjoy your Ubuntu.
```
grep menuentry /boot/grub/grub.cfg
```

---

### Post by shuttleworthwannabe on 2012-04-07
Google grub customizer;  it has a PPA and will do what you want in GUI. THe other is installing UbuntuTweak (allows you to clean up old kernels in a GUI. Read all the instructions carefully before jumping into these third party apps.

---

