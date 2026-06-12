---
title: "New Help - Just installed and"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by daniel000 on 2008-05-21
Hi everyone new to this whole linux setup and yeah installed ubuntu just then.

altho i did use VirtualBox to install it but yeah works fine

the only problem is that i max the screen using ctrl F but when i max it, it is still small on my overall PC 

here is a pic and hopefully someone can help cause i really want to use this OS

[IMG]http://img.photobucket.com/albums/v393/kRaZy-/Ubuntu.jpg[/IMG]

thanks
daniel

---

### Post by daniel000 on 2008-05-21
has it got something to do with my resolution of my monitor as when i installed ubuntu it only gove me the option of installing in 800x600

but my laptop has widescreen has alot more pixles


what can i do ?

i did change my laptop res but still when i get inside ubuntu it still does not go full screen and makes it very hard to go on the net an browse, and other things like that

---

### Post by dingo17 on 2008-05-21
what graphic card do you have??....I think the problem might be the graphic card driver

---

### Post by daniel000 on 2008-05-21
ah k well i have ATI Mobility Radeon x1400....

when i change the resolution to 800x600 it sorta goes fullscreen but just looks stretched an not good ....


hopefully someone can fix this


thanks
daniel.

---

### Post by dingo17 on 2008-05-22
try to install new graphic driver....to do that install ENVY
command to run envy:
> sudo envyng -t

it might want you to turn off gdm....use **rcconf** to get to the menu and then uncross gdm

---

### Post by djben75 on 2008-05-22
I had the same problem until I installed the guest extensions and that seemed to fix it

---

### Post by Sinkingships7 on 2008-05-22
> **djben75 said:**
> I had the same problem until I installed the guest extensions and that seemed to fix it

this will solve your problem. the problem isn't ubuntu. it's the virtual machine.

---

