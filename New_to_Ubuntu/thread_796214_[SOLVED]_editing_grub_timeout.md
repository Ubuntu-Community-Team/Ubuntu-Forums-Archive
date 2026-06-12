---
title: "[SOLVED] editing grub timeout"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by stalkingwolf on 2008-05-16
I seem to be suffering from cranial flatulation.  I cant remember
how to edit the grub menulist to change the time out.  I am setting up a dual boot system for a friend of ours and want to give her
extra time to choose. At least until she gets used to it.

It is 7.10 Ubuntu & 7.10 edubuntu

---

### Post by Dr Small on 2008-05-16
Edit /boot/grub/menu.lst and change "timeout x" to whatever number you want.

---

### Post by tacutu on 2008-05-16
edit /boot/grub/menu.lst and change the timeout value

---

### Post by drs305 on 2008-05-16
System, Admin, Startup Manager, Boot Options. Tick 'Use timeout in bootloader" and specify a time.

If you don't have startupmanager:
```
sudo aptitude install startupmanager
```

While you are there, you can go to the last tab (Advanced) and change the number of kernels you see in the boot menu on start up.

---

### Post by Joeb454 on 2008-05-16
True startup manager may be useful, though if you only want to edit the timeout, just run ```
gksudo gedit /boot/grub/menu.lst
``` and edit the timeout :)

---

### Post by stalkingwolf on 2008-05-18
Thanks to all of you.  That was one of the last bits I needed.
Now on Wednesday I can deliver this system to our friend and her
daughter.  They dont know its coming>:)

again Thanks to all.

---

### Post by stalkingwolf on 2008-06-08
Just an update.  They love it.  I have not even gotten a
"how do you do....." call.  Once I installed the sound card
that I forgot they really loved it.

---

