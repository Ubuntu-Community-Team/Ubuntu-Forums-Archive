---
title: "Audio Disks dont seem to mount properly."
date: 2008-05-11
forum: New to Ubuntu
---

### Post by hovzio on 2008-05-11
Hi, wanted to try a new program (abcde) to rip audio cds. (wanted a console based program other than soundjuicer) Now when I try to access /media/cdrom0 or dev/cdrom0 abcde tells me there is no volume mounted.
So after inserting the cd I rightclick prefences on the desktop icon "audio disk" and take a look in the volume and drive tab.There it tells me the cd is not mounted.I double click audio disk and soundjuicer pops up and starts ripping the album. Other than that I have no access to the cd, I cannot open the folder to see the contents of the disk. I dont really want to use soundjuicer and why can this program access the album when nothing else can? Ive manually created a mountpoint and tried mounting the cd there but that didnt work although im not sure i specified the right filesystem.(mount -t iso ??) I am new to linux and would appreciate any help on the  matter, thanks :)

---

### Post by warbread on 2008-05-11
Press ALT + F2 and type in 'gconf-editor'.  Then go to desktop -> gnome -> volume manager.  Scroll down the options on the right until you see "autoplay_cda_command" and next to it there should be "soundjuicer -d %d".  You can either click on the checkmark above it to disable audio cd autoplaying or double click on "soundjuicer" and change that to "abcde cd:///" and that should solve your problems.  

Let me know if you need more help than that.

---

### Post by hovzio on 2008-05-11
Thanks, worked great for abcde. How can I set it up to just open up in nautilus?

---

### Post by warbread on 2008-05-11
Do the same thing but replace "abcde" with "nautilus".  Make sure to keep the cd:///.

---

