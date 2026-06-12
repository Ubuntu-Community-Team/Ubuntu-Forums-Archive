---
title: "Ubuntu 16.04 LTS Freezing"
date: 2017-10-15
forum: New to Ubuntu
---

### Post by jamesbondhimself on 2017-10-15
I have a HP Pavillion G6 laptop and i recently installed Ubuntu on it but if i watch a YouTube video or play a game it wil freeze.(Those were some examples)
My Specs: Memory:5,3 GiB
     Processor:AMD A6-3400M APU with Radeon(tm) HD Graphics × 4 Graphics:
                     Gallium 0.4 on AMD SUMO (DRM 2.49.0 / 4.10.0-37-generic, LLVM 4.0.0) 
       OS Type:64-bit
             Disk:486,3 GB      
                     (I am running Ubuntu from an external Hard Drive)

---

### Post by Autodave on 2017-10-15
When you say "play a game", are you talking about an on-line game? Firefox had some issues with a recent release. Check and see if you are running Firefox version 56.0 or higher. If not, update it.

In a terminal run:

sudo apt-get update
sudo apt-get upgrade

Reboot and see if that fixes it.

---

