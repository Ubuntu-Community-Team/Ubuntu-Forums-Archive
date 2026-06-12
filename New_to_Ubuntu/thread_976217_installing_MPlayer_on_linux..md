---
title: "installing MPlayer on linux."
date: 2008-11-09
forum: New to Ubuntu
---

### Post by vigya on 2008-11-09
hi.. i just installed ubuntu 8.04 so i am an absolute beginner.
i was trying toinstall MPlayer, of which i have a tar.bz2 file. i extracted it and ran the configure file. it says 'unable to execute the c executables'.
i read the README and it asks me to install the codecs in /usr/local/lib/codecs.
i tried doing it from the root terminal but wasn't successful. actually i attempted at shifting the whole of MPlayer folder. but it din't happen.
What exactly am i supposed to do??

---

### Post by Steve1961 on 2008-11-09
your trying to do this the hard way.  Just add the medibuntu repository to you /etc/apt/sources.list.  Then open a terminal and type:

sudo apt-get update
sudo apt-get install mplayer w32codecs

To add medibuntu open a terminal and type:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add -

Then type:

sudo gedit /etc/apt/sources.list

Add this to the end of the file:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

---

