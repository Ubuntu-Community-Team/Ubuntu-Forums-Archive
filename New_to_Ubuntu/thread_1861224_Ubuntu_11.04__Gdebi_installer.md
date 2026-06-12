---
title: "Ubuntu 11.04  Gdebi installer"
date: 2011-10-15
forum: New to Ubuntu
---

### Post by mokman on 2011-10-15
I have U9.04 installed on Hard drive. Using 11.04 from pendrive. Now 11.04 has no Gdebi installer, how am i supposed to install .deb  packages?

My internet connection is bad and that's why i need a solution that doesn't involve connecting to internet everytime i am using 11.04 from pendrive.

So the appropiate question is,"How do i install .deb packages(ark,comix,p7zip,unrar,vlc etc)
without gdebi installer and without internet connection"

---

### Post by Lisiano on 2011-10-15
3 ways.
1) Use the command line tool dpkg
```
sudo dpkg -i debfile.deb
```
2) Install gdebi using dpkg
```
sudo dpkg -i gdebi.deb
```
3) Use Ubuntu Software Center, when you open a deb file, USC will ask if you wish to install it.

EDIT: There is also a 1337 way of manually extracting, reading where the files should go, putting them there, making some changes to dpkg so it knows the program is installed, but I won't go into how to do that.

---

### Post by tanzoo7 on 2011-12-26
i have access internet in windows 7. I also install ubuntu 11.10 inside windows but problem is my modem does not allow internet in ubuntu. So i cant install gdebi. Do you know how to install gdebi offline.

---

