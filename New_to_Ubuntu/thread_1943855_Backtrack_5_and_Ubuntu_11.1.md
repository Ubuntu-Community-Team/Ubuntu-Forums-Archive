---
title: "Backtrack 5 and Ubuntu 11.1"
date: 2012-03-20
forum: New to Ubuntu
---

### Post by PashConscious on 2012-03-20
Hi guys,

 I am currently installing Back|Track 5. 

When I installed Ubuntu i allocated 500gb of my 750gb for Ubuntu, with the remaing 250156 to be for BT5. I have now come to install BT5 and the default paritioning option was to install it to the existing UB partition. I have had problems before with partitions all over the place so I chose to install it on the remaining space.

Is this likely to cause me any problems? I have read somewhere about bootloaders etc. and I selected the space to install to as logical not primary. Am I in for a shock when I try and boot it up?

Many thanks in advance, you guys are awesome :D

---

### Post by howefield on 2012-03-20
Sounds like you are too late to worry about that now :)

I think Backtrack uses grub 1.98 whereas Ubuntu 11.10 uses 1.99, but you *should* be ok.

---

### Post by PashConscious on 2012-03-20
hmmmmm I dont know which one to choose from the grub loader now.

How do I edit them? I want Ubuntu to be my main OS with BT being an optional second.

I really should look into these things first, what a tit. Sorreee

---

### Post by grahammechanical on 2012-03-20
Install Grub Customizer in the Ubuntu and run it every time you need to put Ubuntu back as the default OS.

[http://ubuntuforums.org/showthread.php?t=1664134]("http://ubuntuforums.org/showthread.php?t=1664134")

It works for me and I have 5 versions of Ubuntu on my hard disk. In fact I used it just now. Last night an update to a 12.04 install updated its Grub and that put its Grub into the MBR and the 12.04 install at the top of the list and as the default OS.

So, I booted into my 11.10, ran Grub Customizer, saved the configuration file and the selected File>Install to MBR and now I get a Grub menu that has 11.10 as the default and a nice image as background and larger text. You can set these things with Grub customizer as well. You can also hide (not delete kernels) Grub entries so that you have a much simpler menu list.

Regards.

---

