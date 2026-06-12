---
title: "How to disable a hardware in Ubuntu"
date: 2015-08-22
forum: New to Ubuntu
---

### Post by Vy_Thng_Gia on 2015-08-22
I have disable the touchscreen in Windows and I erase Windows to install Ubuntu, now the touchscreen have back, so I want to ask if there any way to disable a hardware in Ubuntu. If there are, give me the solution and I will thank you very much
:D:D

---

### Post by dino99 on 2015-08-22
you can either blacklist it, or with dconf (install dconf-editor) set it 'off'

lshw & 'xinput all' commands can help to identify the touchscreen reference to blacklist it.

[http://askubuntu.com/questions/661985/touchpad-only-works-after-hibernate](http://askubuntu.com/questions/661985/touchpad-only-works-after-hibernate)

---

