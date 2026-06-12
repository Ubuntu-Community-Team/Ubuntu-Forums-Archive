---
title: "how do I access a drive on a widows box"
date: 2014-07-28
forum: New to Ubuntu
---

### Post by hebertjerome on 2014-07-28
Hello there all and thanks in advance for the help
I have a fresh install of Ubuntu 14.4 on a newly built PC, it runs like a champ
however all of my music is on a windows 8 PC that is on the same network.
what I want to do is copy the music to my Ubuntu box without having to sneaker the files on a flash drive or remove the drive and install it into the Linux box to copy the files.
when I go to network in the Ubuntu file manager I can see the drive and even the share I created in windows just for this purpose but I get an error saying that Ubuntu doesn't have authorization to access the share.
I set the share up to be accessible to the public with no password but that doesn't seem to help.
how do I access my music over the network?
thanks again for all of the help
jfh

---

### Post by stalkingwolf on 2014-07-28
might try teamviewer or the like.

---

### Post by shane-p-kelly7 on 2014-07-28
So simplest thing I have done for transferring files from windows to Linux over a network is host this very simple and unsecured windows ftp server [http://www.sentex.net/~mwandel/ftpdmin/](http://www.sentex.net/~mwandel/ftpdmin/).  Then, given that you can ping the other computer, you should be able to  type [ftp://192.168.0.1](ftp://192.168.0.1) but with the ip of the windows computer into a browser and then you will be able to navigate files and download.  If you already have an ftp client then you should probably use that but if not this is a pretty easy option.  There are better instructions in that link.

---

### Post by FroggleWoggle on 2014-07-28
Take a look at [this]("https://wiki.ubuntu.com/MountWindowsSharesPermanently"), might help

---

