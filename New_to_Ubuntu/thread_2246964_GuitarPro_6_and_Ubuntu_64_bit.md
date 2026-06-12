---
title: "GuitarPro 6 and Ubuntu 64 bit"
date: 2014-10-04
forum: New to Ubuntu
---

### Post by gleb5 on 2014-10-04
Hi,

I've faced with the problem of the installing of .deb package on the Ubuntu 64 bit system (according to other posts its very common - but following some faqs I still have not been able to solve this issue). Are there anybody here who uses guitar pro on their 64 bit Ubuntu? I'll be very thankful for any suggestions regarding installation.

Gleb

---

### Post by gleb5 on 2014-10-05
Hi,

I've been solved it.
Now I'm only looking for the possibility to associate each gp file with the guitar pro program (on default it associated with tux guitar now). I've make some modification of
gksudo gedit '/usr/share/applications/GuitarPro6.desktop'

> [Desktop Entry] 
Encoding=UTF-8 
Name=Guitar Pro 6 
Comment=Tablature Edition Software 
Exec=/opt/GuitarPro6/launcher.sh %U 
Terminal=false 
X-MultipleArgs=false 
Type=Application 
Icon=guitarpro6.png 
Categories=Application;AudioVideo;


but nothing happens :) also no link in the Applications exits. What should be changed besides?

---

### Post by Vladlenin5000 on 2014-10-05
Have you tried simply right-clicking one of those files, Properties and them change it in th "open with..." tab?

---

### Post by MartyBuntu on 2014-10-05
I use quite a bit of guitar software in Ubuntu Studio, but have never had much luck with Guitar Pro in WINE...

---

### Post by gleb5 on 2014-10-05
right click on GTP -> select another application -> no guitar pro in the list :)
also as I've mentioned above I didn't see it in the applications menu so it seems I should to add it manually but have no ideas how to do is :( so I have to run guitar pro manually from the /opt/GuitaPro6/GuitarPro

---

### Post by Vladlenin5000 on 2014-10-05
The suggestion was to right-click the files you want to open with GuitarPro, not the executable or other files. Depending on how you installed it may not show up as an alternative app for that specific file but you have the option to select other and navigate to its path which appears to be the one you just posted...

---

### Post by gleb5 on 2014-10-05
Hi,

Yes I've followed this idea but there is no guitar pro in Other list because Guitar pro is also absent in the Applications. Is it possible to provide a new link to this list for guitar pro by means of editing of some config file?

---

