---
title: "Ubuntu 8.04 breaking down!"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by CJay554 on 2008-05-10
[SOLVED]
::For solution scroll to bottom::


I upgraded to ubuntu 8.04, everything has been working fine until 2 days ago, i noticed my audio is always on mute, and when i try to unmute it, it compains that GStreamer plugin was not found ( I just did an update with new GStreamer plugins, still nothing...). Other than that, my usual user does not have sudo privilages anymore, i suspect Virtual Box, since i had to add this user to vboxuser to use vbox. Also when i restart my XServer (wether logging out or ctrl + alt + backspace) i try to relogin, and it hangs at a blank screen with a white box at the top left of the screen about 200x200px, i have to do a complete reboot in order to log in again.

Any help would be greatly appreciated!

---

### Post by CJay554 on 2008-05-10
Solved the sudo problem, somehow the user was removed from the admin: in the /etc/group file.

Still at large about the audio and the second login freeze...

---

### Post by kansasnoob on 2008-05-10
Well, just about 2 days ago there were some updates to gstreamer (good).

Just maybe you should check synaptic to see what's up.

I install everything that says gstreamer ----- everything.

Otherwise I don't know.

---

### Post by spiderbatdad on 2008-05-10
You can just add the user to the /etc/sudoers file:
```
sudo visudo /etc/sudoers
```

Add the line: ```
username ALL=(ALL) ALL
```
Where 'username' gets replaced with your actual username.
under #user specifications...under 'root ALL=(ALL) ALL'

---

### Post by CJay554 on 2008-05-10
Yeah, i already installed them, the problem was before i installed the GStreamer plugins, and just a few minutes ago i installed them/restarted, and still nothing with the audio...
Is there a way i can reconfigure ALL my drivers?
like a dpkg-reconfigure ?

doesnt adding a regular user as a sudoer kinda kill the idea of keeping away from root administration unless necessary?

Oh, and on that note, i can't seem to find where to edit my login screen so i can let root to be able to login from there, does 8.04 not support it?

---

### Post by CJay554 on 2008-05-10
Alright... i managed to fix the freezing on 2nd login... I had to go to compiz advanced desktop effects, and enable logging in and logging out... that is a very odd place to be putting an option such as that...

NOW! im still stuck with no sound, help! x.x'

I re-installed the alsa drivers with no improvement, still at mute.

---

### Post by CJay554 on 2008-05-10
Its been a hecktick day today...

1. Solved admin problem by adding my user (bob) to the /etc/group under the admin (with a lower-case a) at the end of the line.

2. I changed a setting in the Advanced Desktop Effects Settings in the System>preferences area. Weird to have it, but they have "Login/Log out" checkbox which i checked and fixed my 2nd login freeze.

3. For audio fix i changed my kernel from 2.6.22.14 to 2.6.24.26 by editing my menu.lst list in the /boot/grub area, and under the ubuntu boot information, i changed the kernel from the given 2.6.22.14 to my other 2.6.24.18, fixed sound being muted and errored with some GStreamer plugin crap.

---

