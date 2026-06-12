---
title: "how to install ati catalyst 9.12 in karmic ubuntu 64 bit"
date: 2010-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by kronictokr on 2010-01-06
BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

BACK UP ANY IMPORTANT INFO!!!!!!!!!!!!!

[COLOR="black"][COLOR="Green"]**Install the fglrx Driver from ATI Catalyst 9.12 For Ubuntu 9.10 Karmic**[/COLOR][/COLOR]


We have to create a folder to enable the instalation process
          location  filename
            VVVV       VVV
create /usr/share/ati "ati"

to do this, enter in a terminal the following command

sudo nautilus

then click "file system" from the left side of the window, then double click the file "usr" and the same with "share". once inside the "share folder, right click on a blank space, click create file, name it "ati".  

leave the nautilus window open while you do the next step

download the 64bit driver from this link
VVVVVVVV
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-12-x86.x86_64.run)

now copy the downloaded file, or drag it into the file you created , (/usr/share/ati  <location reminder )still open in your nautilus window.

when you have placed the "ati-driver-installer-9-12-x86.x86_64.run" file into /usr/share/ati , close your nautilus window, and type the next command into a terminal.

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

this will take a couple minutes as it gathers the proper pakages for your ati gpu. it will create debs and a change log , that will install with the following method

sudo dpkg -i *

there will be missing dependancies, go to SYSTEM>>>SYNAPTICS , and select edit top left , scroll down to and click on fix broken pakages. the click on apply, and lastly click on reload.

now go back to your terminal (to ensure ALL neded pakages are installed, and correctly follow this process exactly)
so, like i was saying, in your terminal, enter the following commands

sudo dpkg -i *

sudo aticonfig --initial

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic


sudo dpkg -i *

sudo aticonfig --initial

sudo reboot

MAKE SURE TO COMPLETE ALL THE STEPS BEFORE YOU REBOOT!!

AFTER YOU REBOOT
vvvvvv
to confirm , in a terminal type

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4200
OpenGL version string: 3.2.9232

if you get errors, 
do this again, but i suggest you get it right the first time

sudo sh /usr/share/ati/ati-driver-installer-9-12-x86.x86_64.run --buildpkg Ubuntu/karmic

sudo dpkg -i *

sudo aticonfig --initial

sudo reboot



references
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_910_linux.pdf)

---

