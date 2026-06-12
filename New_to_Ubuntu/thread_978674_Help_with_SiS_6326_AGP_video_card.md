---
title: "Help with SiS 6326 AGP video card"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by seanjuan on 2008-11-11
Need to load a driver for my **SiS 6326 AGP video card**. How do I accomplish this in the gnome environment. I've tried using Synaptic with no success. My hardware drivers gui shows no devices being installed. I have also tried using a tool ( I can't remember the name)to change my monitor settings from plug and play to Viewsonic VP150 and graphics card to SiS6326 but when I do that my screen becomes distorted. Screen resolution is currently 640x480 and I need is to be at least 1024x768. Any help will be mucho appreciated

---

### Post by bodhi.zazen on 2008-11-11
Wow, how did you come up with at title of "Ubuntu server" for this thread ?

I changed the title to be more descriptive of the problem and hopefully someone with knowledge of your videocard will see it.

---

### Post by overdrank on 2008-11-11
> **seanjuan said:**
> Need to load a driver for my **SiS 6326 AGP video card**. How do I accomplish this in the gnome environment. I've tried using Synaptic with no success. My hardware drivers gui shows no devices being installed. I have also tried using a tool ( I can't remember the name)to change my monitor settings from plug and play to Viewsonic VP150 and graphics card to SiS6326 but when I do that my screen becomes distorted. Screen resolution is currently 640x480 and I need is to be at least 1024x768. Any help will be mucho appreciated

Hi and if you are using Hardy 8.04 was the tool ```
gksu displayconfig-gtk
```
If this fails you can try and boot into recovery mode and use the xfix option. Recovery mode is usually the second choice from the grub.

---

