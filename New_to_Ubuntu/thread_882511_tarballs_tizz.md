---
title: "tarballs tizz"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by marlan on 2008-08-07
Hi All, I know this has been spoken off before but I am really brand new to Xubuntu, How do I open and compile Tarballs? I downloaded Adobe_flash_player_9_linux.tar.gz I followed the instructions given earlier viz. in the terminal I typed Tar TZVF install_flash_player_9_linux.tar.gz I got a readout stating that it couldn't find the file, so that is where I got stuck, is there any other way I can get Adobe flash player other than with the tarball? if not where did I go wrong? :confused:

---

### Post by Bucky Ball on 2008-08-07
[http://www.pendrivelinux.com/2007/10/12/how-to-open-a-tar-file-in-unix-or-linux/](http://www.pendrivelinux.com/2007/10/12/how-to-open-a-tar-file-in-unix-or-linux/)

You could try a google search, there is a lot of info out there ....

These are the instructions for the latest flash, one at a time in a terminal of course, not all at once ...

> cd /tmp
wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz)
tar -zxvf flashplayer10_install_linux_070208.tar.gz
cd install_flash_player_10_linux
./flashplayer-installer

Take note of this instruction ...

> tar -zxvf flashplayer10_install_linux_070208.tar.gz

... basically (very) replace 'flashplayer10' part with the name of the tar file you are trying to untar for untarring, so you would have;

> tar -zxvf nameofyourtarfile.tar.gz

Good luck and welcome to the forums ... :)

---

### Post by zvacet on 2008-08-07
@ **marlan**

> is there any other way I can get Adobe flash player other than with the tarball?

Yes it is.

```
sudo apt-get install flashplugin-nonfree
```

Or for install more things you will need (if you didn´t install them allready)

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by marlan on 2008-08-07
Thank you very much for your fast replies, I followed the instructions given in the first reply and what do you know? I now have adobe flash player installed. :D

---

### Post by Bucky Ball on 2008-08-07
Love it when a plan comes together! Have fun ... :)

---

