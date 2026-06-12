---
title: "Ubuntu Keyboard Hell !"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by abbas1872 on 2008-08-25
Here goes, I have a Asus K8V-x mobo, athlon 64-2800 Socket 754, 1 Gig ram, nvidia 6200 video card lots of cooling. After a fresh install of Hardy 64bit, compiz fusion running, on about the third boot the system behaves as if the up arrow key is being pressed making it impossible to do anything, sometimes the computer keeps printing the number 7 over and over making it difficult to log in, and the computer beeps every so often.
Had the same issue with Hardy 32 bit, and Ubuntu 7.10 32/64bit. Any help would be welcome. The system works fine from the windows XP partition. I would like to ditch windows completly but with this annoying issue i find myself having to boot back to windows more often. Help.
Have tried changing the keyboard from usb to ps2. Cant even attempt to do a vanilla kernel compile and install because the system keeps inserting the number seven into anything i try ang type.

---

### Post by Crafty Kisses on 2008-08-25
Post the results of > lsusb

---

### Post by abbas1872 on 2008-08-25
will do as soon as i can log in to pc, keyboard issue makes this difficult. when i have done do i just type lsusb in the terminal window as root?

---

### Post by Crafty Kisses on 2008-08-25
You don't need to be root.

---

### Post by abbas1872 on 2008-08-25
abbas@Amd64:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0003 Creative Labs 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

