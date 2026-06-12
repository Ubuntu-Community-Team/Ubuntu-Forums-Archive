---
title: "umm how to install programs ???"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by chaosmage222 on 2008-09-28
how do you install programs in ubuntu like games and stuff like maplestory??????????????????????:confused:

---

### Post by Locke_99GS on 2008-09-28
"Add/Remove..." at the bottom of the Applications menu..

Alternatively, you can use Synaptic Package Manager or apt-get from a terminal.

---

### Post by sirwilliamthenice on 2008-09-28
here is a link that i have bookmarked for when i com eup to problems.. of course the longer you use ubuntu the less you will need to use this cheat sheet.

[http://lifehacker.com/software/ubuntu/how-to-install-anything-in-ubuntu-231105.php](http://lifehacker.com/software/ubuntu/how-to-install-anything-in-ubuntu-231105.php)

hope it helps.

---

### Post by ad_267 on 2008-09-28
Another useful link: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Also I think you are a bit confused. MapleStory is a Windows application. It won't run in Linux, unless you can get it to run in WINE.

---

### Post by Keen101 on 2008-09-28
There are actually a couple of way's to do it.

First/easiest: >Applications >Add/Remove

Second: >System >Administration >Synaptic Package Manager

Third: search for suitible and compatible packages. (.deb files, and .run files)

Fourth: Compile from source
        
in terminal type these when browsed into the source code folder:
./configure
make
make install

compiling from source is kind of a last resort, but not really that hard.
I recommend trying to compile the Adobe Flash Plugin from source for practice.


oh, i forgot about "apt-get install"

once you get comfortable with the terminal the fastest way to install something is to type: "sudo apt-get install something"

---

