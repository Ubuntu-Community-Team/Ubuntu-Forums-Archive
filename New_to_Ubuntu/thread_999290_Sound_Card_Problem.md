---
title: "Sound Card Problem"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by dawiba on 2008-12-01
I'm trying to install the drivers for a Tascam US 122, but so far without success.

I've followed the instructions from the ALSA wiki but to no avail. The instructions are

# open up a shell and change to root (or prepend
# sudo to all instructions) and type in your normal
# users password (or just "su -" with roots password)

sudo -i -u root

# download these two packages (use the appropriate
# package manager for your distribution)

apt-get update
apt-get install fxload alsa-firmware-loaders

# check for the latest package version first
# Updated: 2008-06-12

wget [ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2](ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.16.tar.bz2)

# untar the ALSA firmware package (older versions
# of tar may need to use xjf)

tar xf alsa-firmware-1.0.16.tar.bz2

# move the essential components to a standard
# place (for example a firmware folder), modify for an updated firmware package

mkdir /usr/share/alsa/firmware
cd alsa-firmware-1.0.16 && mv * /usr/share/alsa/firmware


Looking through the wiki, as far as I can tell I have 1.0.17 firmware already installed - it comes as standard with Intrepid.

When I type in 

mkdir /usr/share/alsa/firmware

I get this

david@david-laptop:~$ mkdir /usr/share/alsa/firmware
mkdir: cannot create directory `/usr/share/alsa/firmware': File exists
david@david-laptop:~$ cd alsa-firmware-1.0.16 && mv * /usr/share/alsa/firmware

If I type sudo at the start, I get a message telling me 'command not found'

I assumed that ultimately all I'm trying to do is move the drivers in their folder to the appropriate folder in the file system, so I tried to do it by just dragging and dropping to no avail.

I've also posted over in the Multimedia Forum where I got one reply which, although gratefully received, didn't get me any further forward.

Can anyone here help a poor newbie?

---

