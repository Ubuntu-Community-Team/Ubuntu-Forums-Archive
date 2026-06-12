---
title: "How to install ISO (MATLAB) of linux ubuntu"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by gotmilk on 2012-08-22
Hi,

I have a ISO file (MATLAB) that is Linux only (10.04 LTS Ubutu). But I have no idea how to install it. Its about 5 gigs so I'm not sure if I should burn it because I don't have a CD that can hold that much space. I found a mount software in the software center. But I  don't know how to install it. Any ideas? I tried doing it in ther terminal. When I try to mount the ISO manually ($sudo mount ml2012au.iso /home/gotmilk/Desktop/Matlab_Unix_2012a), it says "Mount: only root can do that." What exactly do I do? If anyone could dumb it down (basically tell me what to type on the terminal) , that would be great because I honestly have no clue on how to install exactly.

---

### Post by Carborundum on 2012-08-22
This should do it:
> sudo mount -o loop [location of image file] [mount-point]The DVD should contain an installation guide detailing the steps from there.

---

