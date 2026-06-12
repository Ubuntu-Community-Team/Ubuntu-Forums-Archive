---
title: "graphics and crossfire drivers"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by bregale on 2008-05-30
hi all i have 64bit version of ubuntu running but i dont know where to obtain the updated grapics drivers and crossfire drivers,
   if anyone can help please keep it simple as i am a novice with linux but i think its great 
            thanks

---

### Post by cprofitt on 2008-06-01
> **bregale said:**
> hi all i have 64bit version of ubuntu running but i dont know where to obtain the updated grapics drivers and crossfire drivers,
   if anyone can help please keep it simple as i am a novice with linux but i think its great 
            thanks

Not sure if they support crossfire or not but the first step for a new user should be to enable the restricted drivers.

System | Administration | Hardware Driver

You should then see an option (or options) for any hardware that you have that Ubuntu has detected 'restricted' (meaning non-open source drivers) for. If you enable them they will be downloaded, installed, and configured.

If not you can go directly to the ATI site or use synaptic to install Envy (a program that assists with the install of ATI/Nvidia drivers)

I hope this helps.

---

