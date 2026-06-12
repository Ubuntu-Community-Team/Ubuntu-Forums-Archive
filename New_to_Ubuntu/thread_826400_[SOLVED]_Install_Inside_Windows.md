---
title: "[SOLVED] Install Inside Windows?"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Techpenguin on 2008-06-11
Hey Everybody, I was just wondering exactly how installing Ubuntu inside windows affects windows. Does it mess with your files or affect windows in any way? also, will you be able to boot from it?
please give me a pretty exact list of possible effects. Thanks

---

### Post by tamoneya on 2008-06-11
it depends on exactly what you mean by "install inside windows".  If you mean use wubi to install ubuntu it does not change windows at all.  It creates its own partition and modifies the bootloader.  When you run windows it is as if ubuntu doesnt exist.  If you mean the use of a virtual machine like vmware or virtual box with a ubuntu guest install it is a little different.  When running ubuntu windows will be clearly visible and running.  While just windows is running you will have some multiple gigabyte files lying around on your harddrive.

---

### Post by Joeb454 on 2008-06-11
Using Wubi or VirtualBox/VMWare will leave Windows just as it is (but with a few GB's less space ;))

I've never tried Wubi myself, though I hear it's great for installing, as you don't need to mess with partitions :)

---

### Post by Techpenguin on 2008-06-11
I mean that when you insert the live CD with windows booted the window pops up with the button install inside windows. sorry, that's as specific as I could get

---

### Post by aktiwers on 2008-06-11
It will create a file on your hard drive that works like a Virtual hard drive. It won't change anything.
Then it will install Ubuntu on this virtual hard drive and add it to the windows boot.ini file.

Thats all..  you can even remove it again using the same installer or manually delete the virtual hard drive file and edit the boot.ini file. First one is easier though :)

---

### Post by Techpenguin on 2008-06-11
Thanks!

---

### Post by tamoneya on 2008-06-11
> **Techpenguin said:**
> I mean that when you insert the live CD with windows booted the window pops up with the button install inside windows. sorry, that's as specific as I could get

that would be the wubi method.

---

### Post by Techpenguin on 2008-06-11
Ok Everybody, now I have the follow up problem. because I clicked help me boot from cd a while before when I was testin Ubuntu out, now I have a permanent partition for Ubuntu that isn't the wubi one, but Wubi seems to think it is because it won't make another boot option. I don't know how to delete that boot option, so how do i fix this?

P.S. sorry for unmarking as solved.

---

### Post by Quarg on 2008-08-13
i realize this is old, but just delete the partition and try it again

---

