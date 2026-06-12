---
title: "how to compile xfer9860-0.2.1"
date: 2010-09-16
forum: Programming Talk
---

### Post by mauro24 on 2010-09-16
I don't know if I'm in the right place, but I bought this casio slim fx 9860g, it's a graphing calculator and I would like to be able to program it with ubuntu.  I found this programs source at this website [http://sourceforge.net/projects/xfer9860/](http://sourceforge.net/projects/xfer9860/) where you can "compile" it, and install it to support this calculator for ubuntu.  I'm not a programmer so I need a lot of help.  I have a ubuntu 10.04 64 bit.  Thanks in advanced.

---

### Post by benson444 on 2010-09-17
If you've never compiled anything before you'll probably need to install the gcc compiler along with scons and libusb-dev, which the INSTALL file says you need:
```
sudo apt-get install gcc scons libusb-dev
```
Change directory to where you extracted xfer:
```
cd ~/Downloads/xfer9860-0.2.1
```
Then try to compile it:
```
scons -Q
```
If it doesn't compile then you'll need to install some other package(s). You'll probably get some message about what you're missing. Search for, and then install it:
```
apt-cache search xxx
sudo apt-get install xxx
```
Run xfer with
```
src/xfer9860
```
If it works OK then copy the executable to a directory that is in your PATH so that you can run it from anywhere:
```
sudo cp src/xfer9860 /usr/bin/
```
Now you can run it from any directory by just typing:
```
xfer9860 <...>
```

---

### Post by mauro24 on 2010-09-17
Thanks for your, everything went fine until I had to copy the executable:

~$ sudo cp src/xfer9860 /usr/bin/
cp: cannot stat `src/xfer9860': No such file or directory

After compiling I didn't get any errors, when i execute it i get this:

/Downloads/xfer9860-0.2.1$ src/xfer9860
--- xfer9860 v0.2.1  Copyright (C) 2007 Andreas Bertheussen and Manuel Naranjo.
--- a Casio fx-9860G (SD) communication utility.
Usage: xfer9860 <action> destname [-t throttle]
Calculator actions:
 -u srcname	Upload file `srcname' from disk to `destname' on device.
 -d srcname	Download file `srcname' from device to `destname' on disk.
		Note that this is significantly slower than uploading.
 -i		Shows information about the connected calculator.
 -o		Optimize the storage memory (garbage collection).

Parameters:
 -t value	Throttle setting. The value specifies the delay in ms between
		packets. Default is 0. Try increasing this in case of problems.

Other:
 -h		Display this help message.
 -a		Display info about xfer9860 and its licensing.

~/Downloads/xfer9860-0.2.1$
 
Which still is aconfusing for me, I was waiting for a graphic interface, but I guess i have to learn the hard way.  Thanks anyways for your time.  I'm going to try to test it.

---

### Post by mauro24 on 2010-09-17
Never mind I got the executable copied to user/bin, I was in the wrong directory.

---

### Post by mauro24 on 2010-09-17
when I run th xfer9860 -i comand this what i get:


~$ xfer9860 -i
--- xfer9860 v0.2.1  Copyright (C) 2007 Andreas Bertheussen and Manuel Naranjo.
[>] Setting up USB connection.. 
ERR: usb_set_configuration(): -1

[E] A listening device could not be found.
    Make sure it is receiving; press [ON], [MENU], [sin], [F2]

The calculator was on receiving mode, I don't what do do help!

---

### Post by benson444 on 2010-09-18
It could be a permission issue. The INSTALL file says that you may have to run it as root:
```
sudo xfer9860 -i
```

---

### Post by Jagoly on 2011-03-12
Sorry to bring up an old thread, but it was never resolved. My mum bought one of these calculators. Running as root still gives

```
jagoly@Jagobuntu:~/Desktop$ sudo xfer9860 -i
--- xfer9860 v0.2.1  Copyright (C) 2007 Andreas Bertheussen and Manuel Naranjo.
[>] Setting up USB connection.. Connected!
[>] Verifying device.. Failed.
```

I really don't like having to use windows for this. can't get it working in wine.

---

### Post by flyingfisch on 2012-01-06
Yes, I am having this exact problem, here is my error:

```

flyingfisch@flyingfisch-office-computer: sudo src/xfer9860 -i
[sudo] password for flyingfisch: 
--- xfer9860 v0.2.1  Copyright (C) 2007 Andreas Bertheussen and Manuel Naranjo.
[>] Setting up USB connection.. 
ERR: usb_set_configuration(): -110

[E] A listening device could not be found.
    Make sure it is receiving; press [ON], [MENU], [sin], [F2]

```

---

