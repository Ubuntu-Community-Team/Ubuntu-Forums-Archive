---
title: "Adding Studio to my Hardy Install"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by dreamof3d on 2008-08-10
I recently added Studio to my Hardy install and can't start my NVIDIA driver install. Says I am missing kernel source. If I hit ESC at the grub start, I can still boot into my previous 2.6.24-19 generic, and even have access to the studio programs. At the top of the list is 2.6.24-19-rt and this tell me I don't have the kernel source, and will most likely want the libxxxx headers as well. Is there any way to install these in the 2.6.24-19-rt recovery mode so I can compile my  Nvidia 177.13 drivers.

Another option would be removing that entry from the top of the list in grub.

Any Takers ? Please, it's killing me having to babysit each boot with the escape key.................Thanks

---

### Post by carlinuxlearner on 2008-08-12
(this assumes you have the "universe" repository enabled)

Try using "[envy]("http://albertomilone.com/nvidia_scripts1.html")" to install your nvidia drivers.

Boot up the recovery mode kernel and enter this.

```
sudo apt-get install envyng-gtk
```

once it's done installing run by typing in this

```
envyng -t
```



C@RL

---

