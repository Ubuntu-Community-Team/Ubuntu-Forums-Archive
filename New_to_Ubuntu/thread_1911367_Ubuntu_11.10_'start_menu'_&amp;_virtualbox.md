---
title: "Ubuntu 11.10 'start menu' &amp; virtualbox"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by rigidigital on 2012-01-18
just installed Ubuntu , am a little confused as to where to go for list of programs that are installed to activate with one click such like the windows method where u click on start. Is Gimp installed ?

I cannot see the DVD drive, nor when i load a cd/dvd does anything happen.

I think the dvd problem may be more to do with Sun/Oracle VirtualBox which I am using for the first time to run  Ubuntu on my Win 7 pc.

I have tried to register at the VirtualBox Forum, but the anti-spam
box you have to put in latest version , when I try 4.0.16 it's never accepted ?


ps. the 11.10 desktop is  something other than Gnome or KDE ?

---

### Post by lechien73 on 2012-01-18
The Gimp is not installed by default on Ubuntu, but you can get it from the Software Centre, or by opening a terminal window and typing:

```
sudo apt-get install gimp
```

If the DVD drive is not visible and nothing happens when you load a disc, then have you connected your drive in the virtual machine settings? Try clicking on the **Devices** menu when Virtualbox is running, and see if you can connect the drive from there.

Programs are accessible by clicking on the Ubuntu logo in the sidebar. When they're running, you can right-click on the icon in the sidebar and click **Keep in launcher** and then launch the program with one click after that.

---

### Post by rigidigital on 2012-01-18
[IMG]https://picasaweb.google.com/101974250634128960786/January192012#5699176728677570002[/IMG] thanks Matt, still not sure where on desktop to do what to see all installed apps :redface::redface::redface:

for dvd/cd , I looked under devices and dvd drive is correctly  selected. I also have xp in a virtualbox and have same issue. actually can't even use the dvd drive if i have virtualbox running.
i have to turn off virtualbox machines to access it.

i still cant make the v-box version number take , to join that forum?

[https://picasaweb.google.com/101974250634128960786/January192012#5699176728677570002](https://picasaweb.google.com/101974250634128960786/January192012#5699176728677570002)
[IMG]http://i1095.photobucket.com/albums/i464/Micheal_Lynch/ubuntustart.png[/IMG]

---

### Post by wolfen69 on 2012-01-18
> **rigidigital said:**
> still not sure where on desktop to do what to see all installed apps :redface::redface::redface:



You can hit the windows key, or go to the upper left and hit the ubuntu logo. Then More Apps>Installed>see more results. That will show you what you have. Or, if you know something is installed, just hit the windows key and start typing the name of what you want and hit enter when it shows up in the first spot.

---

