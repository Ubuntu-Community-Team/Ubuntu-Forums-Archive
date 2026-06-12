---
title: "modprobe: FATAL: Module snd-aloop not found"
date: 2022-10-08
forum: Packaging and Compiling Programs
---

### Post by cerdtmann on 2022-10-08
Hey ich versuche "modprobe snd-aloop pcm_substreams=1"  auszuführen, leider erhalte ich immer einen error und komme nicht mehr  weiter. Ich habe es sowohl bei mir im localen Linux versucht als auch auf meinem  Ubuntu Server wo ich es dann auch zum laufen bringen will. Kann da jemand weiterhelfen?

(Ubuntu 20.04.5 LTS):  
modprobe: FATAL: Module snd-aloop not found in directory /lib/modules/5.4.0Ich habe gelesen snd-aloop ist in linux-image-extra und versuchte es also zu installieren:
auf dem server: 
root@v33476:/home/youtube# sudo apt install linux-modules-extra-$(uname -r)
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package linux-modules-extra-5.4.0
E: Couldn't find any package by glob 'linux-modules-extra-5.4.0'

---

