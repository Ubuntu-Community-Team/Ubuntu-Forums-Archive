---
title: "Plustek OpticPro 1248U flatbed scanner"
date: 2006-06-08
forum: Outdated Tutorials &amp; Tips
---

### Post by tubunu on 2006-06-08
============================================
**How to get your Plustek OpticPro 1248U flatbed scanner to scan**
============================================

[COLOR="Sienna"]**EDIT:** Works under Hardy, Intrepid, Jaunty, Karmic, Lucid, Natty and **Oneiric**, too![/color]


1. First, type this in your terminal:
```
sudo apt-get install sane-utils
```

2. Now type the following:
```
scanimage -L
```

This should list your scanner device as
```
device `gt68xx:libusb:001:003' is a Plustek OpticPro 1248U flatbed scanner
```

3. Download **ccd548.fw.zip** (see attachment) to your /home directory, extract it and then copy ccd548.fw it to:
/usr/share/sane/gt68xx

To do this, type this in terminal:
```
$ cd ~
$ sudo cp ccd548.fw /usr/share/sane/gt68xx
```


[COLOR="Sienna"]EDIT 2: If it gives you access error, enable read and write access permission, i.e:  [/COLOR]

```
user@lucid:~$ cd /usr/share/sane/gt68xx/
user@lucid:/usr/share/sane/gt68xx$ sudo chown [COLOR="Red"]user[/COLOR] -R ccd548.fw
```

[COLOR="Red"]*user = your user name[/COLOR]

Now, go to Applications/Graphics/Simple Scan and scan away! =D>

---

### Post by tubunu on 2010-05-16
I posted this how to a while ago and the above method worked for four years on every single Ubuntu distro (Dapper through Karmic), but it doesn't seem to work on Lucid any more... :(
When I open XSane (which I've always used successfully with the scanner) it says: 
"Failed to open device 'gt68xx:libusb:004:002': Invalid argument."

Here's my output from the Terminal: 
```
user@lucid:~$ scanimage -L

device `gt68xx:libusb:004:002' is a Plustek OpticPro 1248U flatbed scanner

```
```

user@lucid:~$ sane-find-scanner -p 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x07b3, product=0x0401 [600dpi USB Scanner], chip=GT-6816) at libusb:004:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # No Mustek parallel port scanners found. If you expected something
  # different, make sure the scanner is correctly connected to your computer
  # and you have apropriate access rights.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

What gives?

---

### Post by tubunu on 2010-05-16
A solution!!! :)
It turned out that the file ccd548.fw could only be accessed by root. So in order to be able to scan, I had to give myself read and write access permission. To do that: 

```
user@lucid:~$ cd /usr/share/sane/gt68xx/
user@lucid:/usr/share/sane/gt68xx$ sudo chown user -R ccd548.fw
```

:guitar:

---

