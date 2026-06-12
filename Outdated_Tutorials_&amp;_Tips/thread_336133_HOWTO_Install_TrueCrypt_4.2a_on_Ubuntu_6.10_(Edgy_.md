---
title: "HOWTO: Install TrueCrypt 4.2a on Ubuntu 6.10 (Edgy Eft) 64bit"
date: 2007-01-11
forum: Outdated Tutorials &amp; Tips
---

### Post by optimus.prime on 2007-01-11
This guide will demonstrate how to install TrueCrypt 4.2a on Ubuntu 6.10 "Edgy Eft". This guide will make some assumptions about your current configuration and I offer no guarantees that it will work for you. Then again, this is Linux, no one ever assumes it'll work for them! ;-)

Assumptions:
[LIST]
[*]You are using the vanilla 2.6.17 kernel
[*]You know how to use the command line (it ain't that hard people!)
[*]I'm using the "Edgy Eft" 64bit version, however it should work with the 32 bit without modification (no guarantees however!)
[/LIST]You are using the vanilla 2.6.17 kernel

1. First. head over to [TrueCrypt's website]("http://www.truecrypt.org/downloads.php") and download the **source code**. If you are running on i386 (32bit) then you are sailing, as they have a pre-made deb package. 

2. Next we are going to need a few key tools:

```
sudo apt-get install build-essential dmsetup gawk linux-source linux-headers-`uname -r`
```

Make sure you enter that line *exactly* as shown.

3. 

```
cd /usr/src/
sudo bunzip2 linux-source-2.6.17.tar.bz2
sudo tar xvf linux-source-2.6.17.tar
sudo ln -s linux-source-2.6.17 linux
sudo make -d -C linux modules_prepare
```

As a warning, that third step will send a pile of untared source files across your screen, so long as no errors have occured, you should be fine.

Once that is complete, change back to the directory where you stored the TrueCrypt source code.

4. 

```
tar xzvf truecrypt-4.2a-source-code.tar.gz
cd truecrypt-4.2a/Linux/
sudo ./build.sh

```

The first step will send a butt-load of untared directories across your screen.

Now folks, break out your copies of War and Peace, Quantum Physics 101, Neurosurgey for dummies and anything  else you might have (or just head over to [slashdot]("http://www.slashdot.org")....) as this will take a while. On my AMD 64 X2 3800+ Windsor with 1GB of RAM, the compliation took over 30 minutes.

Assuming no errors were reported, you are golden!

```
sudo ./install.sh
```

Next comes the very easy part, the installation. You can accept the defaults for 99%, however **if you want to run TrueCrypt as a regular user, you will have to change the default!**

```
Checking installation requirements...
/dev/mapper/control not found - create? [Y/n]: **Y**
Testing truecrypt... Done.

Install binaries to [/usr/bin]: 
Install man page to [/usr/share/man]: 
Install user guide and kernel module to [/usr/share/truecrypt]: 
**Allow non-admin users to run TrueCrypt [y/N]: y**
Installing kernel module... Done.
Installing truecrypt to /usr/bin... Done.
Installing man page to /usr/share/man/man1... Done.
Installing user guide to /usr/share/truecrypt/doc... Done.
Installing backup kernel module to /usr/share/truecrypt/kernel... Done.

```

Now, one thing to keep in mind is that this isn't exactly like the Windows version, in that it doesn't have a GUI, everything is done from the command line. However, to get started, type:

```
man truecrypt
```

And you're done! Give yourself a pat on the back!

Bibliography (muchos gracias to the fellows who tread through this before me!)

[http://www.ubuntuforums.org/showthread.php?t=199367](http://www.ubuntuforums.org/showthread.php?t=199367)
[http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/](http://www.howtogeek.com/howto/ubuntu/install-truecrypt-on-ubuntu-edgy/)

---

### Post by kettal on 2007-01-21
Thanks.

I just wish there was a way to do this without compiling the whole kernel. I have a slower machine, and it would be easier to just download a new kernel than compile it myself :(

---

