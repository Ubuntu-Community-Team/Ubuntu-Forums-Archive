---
title: "need help in installing gstreamer"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by NO2 on 2008-06-17
i am new to linux. i am having problems installing gstreamer. i cannot install the modem as no drivers are available for it. i had downloaded the file gstreamer-0.10.19.tar.bz2. where and how do i have to extract it? i extracted it on the desktop and then executed the following command in shell:
./configure
which gave an error which was related to C(cannot compile or something.. i don't remember it exactly.).
do i have to extract the folder to usr/local/src? if so how to do it. i currently know very few shell commands. i am using ubuntu 8.04.

---

### Post by cozmicharlie on 2008-06-17
What exactly are you trying to install?  You mention a modem?  Gstreamer are mainly various codecs so you can play music etc.  You do need them but I am not sure how that fits with setting up a modem.

You are trying to compile from a source file and that maybe a little more than you want to take on until you become more familiar with Linux.  The easiest way to install gstreamer is through synaptic.  You first want to add the Medibuntu repository to your source list then you can add gstreamer from Synaptic or using apt-get.

This post should help you [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) 

If you have problems post back.

Also, this will help you become familiar with the different methods for adding packages (programs) in Linux [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Inxsible on 2008-06-17
> **NO2 said:**
> i am new to linux. i am having problems installing gstreamer. i cannot install the modem as no drivers are available for it. i had downloaded the file gstreamer-0.10.19.tar.bz2. where and how do i have to extract it? i extracted it on the desktop and then executed the following command in shell:
./configure
which gave an error which was related to C(cannot compile or something.. i don't remember it exactly.).
do i have to extract the folder to usr/local/src? if so how to do it. i currently know very few shell commands. i am using ubuntu 8.04.
gstreamer is available in the repos. you do not need to compile from the source. Go to Applications>>add/Remove. Search for "gstreamer" without the quotes and install all of the gstreamer packages. That should do it.

---

### Post by NO2 on 2008-06-18
i cannot install the modem so i cannot use the internet on ubuntu. i downloaded the mentioned file using windows. how can i paste or extract a file or folder in usr/local/src?

---

### Post by cozmicharlie on 2008-06-18
> **NO2 said:**
> i cannot install the modem so i cannot use the internet on ubuntu. i downloaded the mentioned file using windows. how can i paste or extract a file or folder in usr/local/src?

OK - I see your problem. You most likely are missing some dependencies.  In the extracted folder their is usually a "readme" or "install" file that has directions for compiling.  Check this for any necessary dependencies and then go into Synaptic and install them.    

the commands for compiling are:
./configure
make
sudo make install

First open a terminal.
Change directory to the untar folder
# cd /home/yourname/desktop/gstreamer-0.10.19 (just drag the folder into the terminal window after you type cd)
# ./configure
# make
# sudo make install

---

