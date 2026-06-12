---
title: "Have thumb drive. Will travel"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by Kevin McCready on 2012-04-11
I'm still stoked with my new Linux Lubuntu system after all these weeks. I've got it pretty much how I want it now.

So the next thing is to copy it all to a thumb drive so I can boot it on my friends' computers when I go travelling.

Can someone help me transfer my system to a usb? I'd like to be able to have my desktop as it's now set up and all the little tweaks I've made. This is what I've settled on:
Dolphin as File Manager
mplayer in gnome-media (I had to install PulseAudio Volume Control and then select Sound Recorder)
leafpad (brilliant little text editor for HUGE text files)
gnumeric (spreadsheet)
libreoffice-writer (closer to Microsoft word functionality and much better than abiword)
ibus-pinyin (for chinese - it needed tweaking)
mirage for image manipulation
thunderbird (for email)
clipit (so that stuff cut to clipboard buffer is available after I quit the application)
The file manager (PCManFM 0.9.9) is awful and slow (sorry guys). 

Looking forward to the help of the community. I've tried to read the past posts on this but it's all a bit too hard and I'd hate to give up.

---

### Post by mastablasta on 2012-04-11
use remastersys to create your own live system

---

### Post by Kevin McCready on 2012-04-11
Thanks. I searched in Synaptic and it's not there. I'm a bit wary about trying to install stuff which is not in the repository. Could anything else do the job. I don't want to back up my data, just the setup of the system.

---

### Post by androssofer on 2012-04-11
> **Kevin McCready said:**
> Thanks. I searched in Synaptic and it's not there. I'm a bit wary about trying to install stuff which is not in the repository. Could anything else do the job. I don't want to back up my data, just the setup of the system.

perhaps not the solution your wanting to hear, but its what i would do (due to lack of knowing how to actually go about it the way you want)

create a live usb with a few gig extra on it for changes.. boot up the live usb... build the system from scratch from a fresh install on the usb.. it will stay in that state once unplugged..

if you cant find an better alternative, do this. It shouldn't take too long, and uses built in software :-) 

this link should provide any extra info you need:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by MG&amp;TL on 2012-04-11
> **Kevin McCready said:**
> 
The file manager (PCManFM 0.9.9) is awful and slow (sorry guys). 



...odd. Nice and speedy on my machine. File a bug, then try installing thunar or something.

---

### Post by Kevin McCready on 2012-04-11
Thanks everybody for your input. It's all a bit daunting but I think I'll give remastersys a go. I might try uck too.

Re PCManFM, I have a massive directory I use quite often and PCManFM just takes ages before I can do anything with it. Lots of programs default to it to. I installed Dolphin and now I tend to go to Dolphin and launch from there.

---

### Post by daslinkard on 2012-04-11
Kevin,

Actually I like the idea of installing Linux on a Thumb Drive and leaving extra space for updates, downloads, changes, etc.  In fact 16 GB thumb drives are dirt cheap right now and you can store a ton of information.  It has been my experience in the 4 months that I have been using Linux that it becomes easier to set up your system (the way you want it) with each install.

Since I installed Ubuntu on my 1st machine I have probably installed Ubuntu on 10 other PC's either that I own or belong to a friend, customer, etc., and with each install I typically set their Ubuntu install up the same way that I like mine.  It might be a little bit of a pain, but if you have any issues with the repository at all...I suggest going to a Staples or Office Depot and picking up a dirt cheap thumb drive and get to building.

Good luck!

---

### Post by mastablasta on 2012-04-12
you can add a signed repository.
 
[http://www.remastersys.com/ubuntu.html](http://www.remastersys.com/ubuntu.html)
 
[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

### Post by oldfred on 2012-04-12
I prefer a clean install and copy /home for user settings & dpkg for applications list. 

If your flash drive is 8GB or more you can do a full install, otherwise a persistent install is your best choice.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Persistent installs:
HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)
HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)

Full installs.
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Actually a full install to flash drive is just like any install to a second drive. If you have a 16GB flash you can make two 8GB partitions, copy current /home to one partition and as part of the install on the other partition mount but do not format it.

You can reinstall all your current apps:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List is just a text file, so you can manually edit if you want.

---

