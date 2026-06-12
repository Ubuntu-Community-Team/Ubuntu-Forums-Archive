---
title: "Nvidia graphics seem choppy in desktop"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by icouldntfindausername on 2008-06-03
I recently installed Ubuntu 8.04 x64 and I've got a 8800 Ultra. By using EnvyNG I managed to install graphics card drivers (169.12). I see that there are newer drivers on nvidia's website: [http://www.nvidia.com/object/linux_display_amd64_173.14.05.html](http://www.nvidia.com/object/linux_display_amd64_173.14.05.html)
However, I couldn't find a way to install them. Could someone help me with that?

And I also have this problem that when I move windows around etc. the graphics seem all choppy. I get these horizontally lines reminding of playing games without having Vsync enabled. Is there any way I could make things go smoother on the desktop?


Thanks.

---

### Post by spiderbatdad on 2008-06-03
looks like step 1. 2. 3. from the link you provided.
Also, IDK if the package nvidia-xconfig from synaptic would be good for you.

---

### Post by icouldntfindausername on 2008-06-04
I tried following the steps, but when I type "sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run" in gnome-terminal I only get the message "Can't open NVIDIA-Linux-x86_64-173.14.05-pkg2.run". Why is that? I also tried pressing ctrl+alt+backspace, end gdm and enter "sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run" again, but with the same error message.

---

### Post by D4rkSide on 2008-06-04
try put sudo sh NVIDIA-Linux-x86_64-173.14.05-pkg2.run then root will ask for your password.

---

