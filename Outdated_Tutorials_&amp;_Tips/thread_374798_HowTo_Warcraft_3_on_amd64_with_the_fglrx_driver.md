---
title: "HowTo: Warcraft 3 on amd64 with the fglrx driver"
date: 2007-03-02
forum: Outdated Tutorials &amp; Tips
---

### Post by pay on 2007-03-02
Firstly there were a few problems with getting to run Warcraft 3 with the fglrx driver and the anti-piracy technology. I'll explain how to get past these issues with wine. Firstly, install the fglrx driver as per normal. ```
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --overlay-type=Xv
sudo depmod -a
sudo modprobe fglrx
```But now we are going to link the driver libraries to the 32bit folder so 32bit applications can take advantage of them.```
sudo ln -s /usr/lib64/libfglrx* /usr/lib32/
```Now we need to get wine and install it. ```
sudo aptitude install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32 msttcorefonts
wget http://wine.budgetdedicated.com/archive/ubuntu/edgy/wine_0.9.31~winehq0~ubuntu~6.10-1_i386.deb
sudo dpkg -i --force-architecture wine_0.9.31~winehq0~ubuntu~6.10-1_i386.deb
```Now we need to configure wine properly.```
wget http://sidenet.ddo.jp/winetips/files/wine-config-sidenet-1.9.2-test2.tgz
gunzip wine-config-sidenet-1.9.2-test2.tgz
cd wine-config-sidenet
chmod 755 setup
./setup
```I use option 0 but you can use any you want to. Now install Warcraft 3 ```
wine /media/cdrom0/install.exe
```(you might need to change cdrom0) and then patch it to the latest version. For me it wouldn't run, it just told me to put the cd in even though it was in. If this happens to you just download a no cd crack from [www.gameburnworld.com](www.gameburnworld.com) and extract it to your warcraft 3 folder. And finally make a startup script for it. ```
sudo nano /usr/bin/war3
```and past >  #!/bin/sh
# edit the next path
pushd /your/wc3/directory
wine -War3.exe -- War3.exe -opengl
popd inside. To start the game type war3 in.
Hopefully this helped someone:)

---

