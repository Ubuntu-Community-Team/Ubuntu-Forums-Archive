---
title: "Help getting youtube video to work in Ubuntu/Firefox"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by BennyBB on 2008-11-07
I am new to Ubuntu/Linux.  I just install Ubuntu and it is great.  Everything is working well.  Just one thing............

I have the following installed:
Ubuntu 8.10
GNOME 2.24.1
FOXFIRE 3.0.3

I can not watch any youtube videos.  I thought maybe I needed to install flash so I went to flash.com and tried to install.  I followed all the methods and instructions that flash.com has for Ubuntu/Linux installation of flash but was not able to install.

How do I install flash for my system?

---

### Post by ggaaron on 2008-11-07
It's in the repositories GNU flash player is gnash and adobe flash is flashplugin-nonfree. Generally you don't need to install things from outside the repository.

---

### Post by BennyBB on 2008-11-08
Thank you for your response.  I need more information like step by step how do I install these?  I just want the flash plug-in for the browser so I can see the video (not an application to create flash).

---

### Post by Campingman on 2008-11-08
Hi 

A lot of information on all multimedia and video here, should sort you out

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by metallicamike on 2008-11-08
if the file extension you selected is anything other than .deb or .tar.gz, then it wont work

---

### Post by tjwoosta on 2008-11-08
system-administration-synaptic package manager

go to settings-repositories and make sure you have main, universe, restricted, and multiverse selected

then search for "flash"

adobe flash will be listed as flashplugin-nonfree

(before installing you must remove  other versions of flash that you may have installed)

---

### Post by ggaaron on 2008-11-08
> **metallicamike said:**
> if the file extension you selected is anything other than .deb or .tar.gz, then it wont work

And if it's deb then it probably won't work too. Ubuntu is a binary platform and you should only install software compiled for this platform.

tjwoosta showed you the right installation technique - you will install almost everything using this method.

---

### Post by oldos2er on 2008-11-08
"And if it's deb then it probably won't work too."

 Better not let the repository maintainers know that!

---

### Post by kansasnoob on 2008-11-08
I'd begin by going to System > Administration > Software Sources and make sure that, under the "Third Party" tab, Intrepid Partner is "ticked" (not source code).

Then go to Accessories > Terminal and:

```
sudo apt-get --purge remove adobe-flashplugin
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

```
sudo apt-get install ubuntu-restricted-extras
```

NOTE: Change ubuntu to kubuntu or xubuntu if that's what you have!

Optional but personally highly recommended:

```
sudo apt-get install flashblock
```

Then restart Firefox: File > Quit, then restart Firefox. Hopefully you'll now have a working Flash!

---

### Post by ggaaron on 2008-11-08
> **oldos2er said:**
> "And if it's deb then it probably won't work too."

 Better not let the repository maintainers know that!

I don't quite understand what you've meant?

---

