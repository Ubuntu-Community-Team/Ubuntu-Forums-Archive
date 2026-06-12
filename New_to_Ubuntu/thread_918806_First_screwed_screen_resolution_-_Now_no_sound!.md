---
title: "First screwed screen resolution - Now no sound!"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by bumanie on 2008-09-13
Following kernel update to 2.6.24-21-generic, I lost most screen resolution options, but have managed to get that working. Unfortunately, as soon as the resolution was fixed, upon reboot, I now have no sound. Attached is output of lspci. It clearly shows an ati sound card. It worked fine before the kernel update.

---

### Post by bumanie on 2008-09-13
Here's the error message I am getting.

---

### Post by k33bz on 2008-09-13
i have had that once before, took along time for anyone to be able to fix it, hopefully it wont take that long for yours,


First, download the drivers from the alsa website: [http://www.alsa-project.org/main/index.php/Download](http://www.alsa-project.org/main/index.php/Download)

Since you are at it, get also the library and the utilities, to have all of the same version.

Once you have them on your computer uncompress:

Code:

tar -xjf alsa-driver-1.0.16.tar.bz2
tar -xjf alsa-lib-1.0.16.tar.bz2
tar -xjf alsa-utils-1.0.16.tar.bz2

You will need some extra packages for the utilities:
Code:

sudo aptitude install libncurses5 libncurses5-dev

Proceed to each one of the newly unpacked directories
Code:

cd alsa-lib-1.0.16
./configure
make
sudo make install

Code:

cd alsa-driver-1.0.16
./configure --with-cards=hda-intel --with-oss=yes --with-sequencer=yes
make
sudo make install

Code:

cd alsa-utils-1.0.16
./configure
make
sudo make install

Do not remove these directories. You will need them, should you want to remove what you just installed. To uninstall, just run a "make uninstall" inside them.

Configure the new modules
Code:

sudo alsaconf

Follow the instructions.

Reboot and see what happens, check if the modules are loaded
Code:

lsmod | grep -i snd

---

### Post by bumanie on 2008-09-13
Get this error from gcc - looks as though there is no .h in gcc for this kernel. Hmm, not too good at interpreting these things yet. Anyone got any ideas?

---

