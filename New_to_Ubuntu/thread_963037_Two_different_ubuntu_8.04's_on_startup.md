---
title: "Two different ubuntu 8.04's on startup"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by ludu900 on 2008-10-29
I have no clue what happened to ubuntu. In the first screen seen after startup which allows me to choose windows or ubuntu, there are two different ubuntus. They each have a long string of numbers but one ends with 04 24-21, the other with 04 24-19. I do not know what the difference between the two is. I had been using the 21 version, but for some reason when i decide to use that version, it now says that the file can not be found and takes me back to the initial screen. I have a broadcam network card and installed a driver and had it working. In the 19 version, everything else is the same as the 21 but the driver has mysteriously disappeared. Also when using the 19 one, i am taken directly to a command prompt like screen. It took a lot of experimenting with commands to get to the actual ubuntu interface, but i finally did with the "shutdown now" commmand. I am completely lost and really want to use ubuntu but have sadly been forced to windows. 
Any idea what is going on????

---

### Post by aktiwers on 2008-10-29
That is your old kernel you see there. Ubuntu leaves it there, if the new one (which you got from an update probably) did not want to boot. But it seams like it does, so don't worry about it. :)

---

### Post by Zzl1xndd on 2008-10-29
Linux keeps each revision of your Kernel so every time it is upgraded another entry is added to the list. This is mostly a safety feature in case something goes wrong with an upgrade you can move back to the old version.

---

### Post by ludu900 on 2008-10-29
Ok, that makes sense. I still do not understand why the new one will not work and why the old one kept all of my old settings and programs but not the broadcam driver.  That is the main thing that I need right now.
Do you know why when the old Kernel boots it goes directly to the a command prompt screen?

---

### Post by majickmann on 2008-10-29
Actually, you should see four versions of ubuntu, in addition to your windows operating system in the menu.
Each of the two kernel versions should have a "recovery mode" for the total (four).
It would be very difficult, if not impossible to help without some information.
The "missing file" could mean that the initrd.img file has been renamed, deleted, or otherwise corrupted.
The possible reasons abound, but usually because the upgrade was interrupted.
If you do have a recovery mode option, select it.  You can find detailed instructions in Ubuntu documentation or search the forums.
If you have backed up your data or dont' have any significant data, do a clean install of the latest Ubuntu version.
Hope this helps...
--majickmann

---

### Post by kansasnoob on 2008-10-29
[QUOTE=ludu900;6060545]I have no clue what happened to ubuntu. In the first screen seen after startup which allows me to choose windows or ubuntu, there are two different ubuntus. They each have a long string of numbers but one ends with 04 24-21, the other with 04 24-19. I do not know what the difference between the two is. I had been using the 21 version, but for some reason when i decide to use that version, it now says that the file can not be found and takes me back to the initial screen. I have a broadcam network card and installed a driver and had it working. In the 19 version, everything else is the same as the 21 but the driver has mysteriously disappeared. Also when using the 19 one, i am taken directly to a command prompt like screen. It took a lot of experimenting with commands to get to the actual ubuntu interface, but i finally did with the "shutdown now" commmand. I am completely lost and really want to use ubuntu but have sadly been forced to windows. 
Any idea what is going on????[/QUO

Each kernel choice should also be followed by a Recovery option. Try the recovery option for ****.21 and let us know what it says.

---

### Post by ludu900 on 2008-10-29
I have the recovery modes and i tried it for the 21 version. It gave me the same screen. I will probably just wait for the 8.10 version to come out and download that.

---

