---
title: "setting up a printer scanner fax"
date: 2016-02-08
forum: New to Ubuntu
---

### Post by jim131 on 2016-02-08
Hi This is my first post and I am new to linux and Ubuntu. I am trying to install drivers for my printer downloaded from the Samsung Australia site with no success. I have managed to get the printer registered on Local host and it is functioning correctly as a printer however I need to set up the Scanner in order to be able to scan and send to Thunderbird as a PDF file attachment. The drivers from Samsung are listed for my printer CLX3185FN and for Ubuntu. My problem is I dont know how or where to install them. I have download  Synaptic package manager but I am not sure how it works or if this is the tool for the job. All advice would be much appreciated. Jim131

---

### Post by Vladlenin5000 on 2016-02-08
Hi and welcome.

What drivers have you downloaded? Link please...
Depending on what those files are, different methods apply.

---

### Post by jim131 on 2016-02-10
Hi I downloaded the following [http://www.samsungsetup.com/TS/Client/en/Install.html](http://www.samsungsetup.com/TS/Client/en/Install.html). thank you for your help. JIM131

---

### Post by Vladlenin5000 on 2016-02-10
It contains several scripts. Extract the file to anywhere (example: Downloads).
Right-click each *.sh file, select properties and make sure all are executable.
Just in case also follow this instructions and change the settings of Nautilus, the file manager, to "Always ask": [https://help.ubuntu.com/stable/ubuntu-help/nautilus-behavior.html](https://help.ubuntu.com/stable/ubuntu-help/nautilus-behavior.html)
Double-click "install.sh" and, should a dialog appear, choose "Run (or Execute) in Terminal" so you can see what's happening.

This should install everything needed for that MFP. Of course, you can always run it all from the terminal but the first steps in a familiar file manager are usually easier for newbies.

---

