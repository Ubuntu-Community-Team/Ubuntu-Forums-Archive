---
title: "Ubuntu 20.4 freeze after few hours of working."
date: 2020-04-25
forum: New to Ubuntu
---

### Post by mouratovpt on 2020-04-25
Hello guys,

Im new in Linux world, leave my windows and starting using Linux, so im sorry if it's a dumb question.

I install a fresh Ubuntu 20.4 LTS, works fine, but after a few hours of normal usage, the system hangs/freeze, only mouse working but i can't do nothing.
I have to shutdown the system by click on power off button.

Anyone knows where i can check the logs or know how to solved?

Im using HP Omen, i have dual boot BUT, linux is in primary disk (hole disk for ubuntu)


Here is the system info.

OS: Ubuntu 20.04 LTS x86_64 
Host: OMEN by HP Laptop 15-dc0xxx 
Kernel: 5.4.0-26-generic 
Uptime: 37 mins 
Packages: 1968 (dpkg), 14 (flatpak), 
Shell: bash 5.0.16 
Resolution: 1920x1080  
DE: GNOME 
WM: Mutter 
WM Theme: Adwaita 
Theme: Yaru [GTK2/3] 
Icons: Yaru [GTK2/3] 
Terminal: gnome-terminal  
CPU: Intel i5-8300H (8) @ 4.000GHz 
GPU: Intel UHD Graphics 630 
GPU: NVIDIA GeForce GTX 1050 Ti Mobi 
Memory: 2881MiB / 15821MiB 
  
Thanks a lot

---

### Post by speartip on 2020-04-25
It may be graphics driver related. Try looking in "additional drivers" and see if it offers to install any extra drivers.
ps. Not 100% certain what it's called in ubuntu as I'm using kubuntu at present.

---

### Post by mouratovpt on 2020-04-25
They have nvidia install.

[ATTACH=CONFIG]285608[/ATTACH]

---

### Post by mörgæs on 2020-04-25
Have you checked if the UEFI firmware needs updating?

---

