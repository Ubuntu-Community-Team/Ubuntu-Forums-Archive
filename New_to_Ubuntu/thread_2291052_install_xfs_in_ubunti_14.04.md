---
title: "install xfs in ubunti 14.04?"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by RoNiNk on 2015-08-17
I try to  sudo apt-get install xfs
and i get error Package 'xfs' has no installation candidate
google say that i have to add repo
so i did echo 'deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) saucy main universe' >> /etc/apt/sources.list.d/extra.list
but when i do apt-get update it cant connect to new repo Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-amd64/Packages](http://archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-amd64/Packages)

---

### Post by howefield on 2015-08-17
Google probably didn't suggest that you add an old expired, end of life saucy repository to a Trusty 14.04 install.

Do you have a link to the information you were trying to follow ?

---

### Post by RoNiNk on 2015-08-17
I try to install maya  [https://gist.github.com/MichaelLawton/ee27bf4a0f591bed19ac](https://gist.github.com/MichaelLawton/ee27bf4a0f591bed19ac)
I get errors when i do 
[COLOR=#333333][FONT=Consolas]sudo apt-get install -y  alien csh tcsh libaudiofile-dev libglw1-mesa elfutils gamin libglw1-mesa-dev mesa-utils xfs xfstt ttf-liberation xfonts-100dpi xfonts-75dpi ttf-mscorefonts-installer libfam0 libfam0-dev
[/FONT][/COLOR]E: Package 'xfs' has no installation candidateE: Unable to locate package libfam0-dev
[COLOR=#333333][FONT=Consolas]
[/FONT][/COLOR]

---

### Post by dino99 on 2015-08-17
[https://launchpad.net/ubuntu/+source/xfs](https://launchpad.net/ubuntu/+source/xfs)   That xfs package was dropped after Precise release

---

### Post by flocculant on 2015-08-17
>  E: Package 'xfs' has no installation candidateE: Unable to locate package libfam0-dev

xfs as a package was last available for the Precise LTS.

Edit - snap ...

More edit - from that page you link
> 
#Didn&#8217;t work but doesn't seem to be a problem
sudo apt-get install -y libglw1-mesa-dev mesa-utils xfs

Which would appear to just be xfs failing to install - tell them.

---

