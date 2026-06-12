---
title: "[SOLVED] virtualbox + sharing music"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-10-15
i use virtualbox to run the zune software for my mp3 player. to save hard drive space since my drive is small i want to share mp3 files between songbird on my ubuntu distro and zune software to sync with my mp3 player...

is this possible?

---

### Post by howefield on 2008-10-15
Have you considered using Virtualboxes shared folders option ?

---

### Post by tjwoosta on 2008-10-15
in virtualbox settings choose the folder that you want to share

then load up the virtualbox guest

not sure about vista, but in windows xp you would right click on "add a netowrk place" and choose "map a new netowork drive"

select the virtualbox shared folder


whatever you do, make sure to map it as a **network drive** not a **network place**


if you map it as a network place there would be an incredible lag

---

### Post by PatrickMoore on 2008-10-15
> **howefield said:**
> Have you considered using Virtualboxes shared folders option ?

i have but not sure the appropriate way to handle that

---

### Post by PatrickMoore on 2008-10-15
im trying now

---

### Post by PatrickMoore on 2008-10-15
i cannot find the virtualbox shared folder

---

### Post by Therion on 2008-10-15
The only way I've gotten shared folders to work in VB is when I set them up during the install.  If I try and do it post-install, I get a BSOD from XP.  

You can try to set up a new network drive in Windows by using the Wizard but since you didn't set up any shared folders in your VM to begin with, I'm not sure that would work...   

Try going into the shared folder section in Virtual Box and see if you can establish a shared folder post install.  If so, then go back into Windows and see if you can connect to it using the New Network Drive wizard. 

If none of this works you may need re-create your XP guest being sure to set up at least one shared folder during the install.

---

### Post by PatrickMoore on 2008-10-15
success no blue screen of death and its syncing all my albums. now i can put all my music on my computer

---

### Post by Therion on 2008-10-16
Awesome.  Glad you got it working!

It would be great if you'd mark the thread "Solved" using Thread Tools up at the top.

---

