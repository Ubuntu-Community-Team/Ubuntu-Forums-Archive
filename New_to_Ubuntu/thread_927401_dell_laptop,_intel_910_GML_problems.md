---
title: "dell laptop, intel 910 GML problems"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by Jesten on 2008-09-22
the way my laptop runs now feel like the vid drivers arnt right. feels like its sluggish. i went to this website. but im a realy noob to linux. [http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html)
i have no clue what they want me to do to update my drivers. the reason i feel like its my vidcard drivers is ive done a lot of windows builds from scratch hardware for myself and family. so i know what no vid drivers feels like. i think what they tell me to type in the term is not correct is get some bash error. any help would be awesome.

Jesten

this is my vid card info
>  *-display:0 UNCLAIMED   
       description: VGA compatible controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 915GM/GMS/910GML Express Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0


---

### Post by willca on 2008-09-23
Is that info about your vga card came from running

lspci | grep VGA

---

### Post by Jesten on 2008-09-23
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 thats what i got when i ran that. i forgot to mention i did open synap and installed everything that had to do with the 915gm drivers

---

### Post by Jesten on 2008-09-26
bump

---

