---
title: "HELP!!! I've done something and can't mount my music drive..."
date: 2008-10-31
forum: New to Ubuntu
---

### Post by murdison on 2008-10-31
Yes, I am indeed a Newb...

today I was trying to figure out how to automount my second internal HD containing my music files, and did something that prevents it from mounting.

I started down this pathway by choosing properties for the drive that was manually mounted to my desktop, and in the details section of the last (drive) tab, I emulated what was in the information above... /media/drive...    anyway, now if I try to mount the drive I get an error, can't mount due to unexpected character (I think the second /)...

I've looked in etc and media to try and identify any config files that may have changed but can't find anything...

Please help... I've spent the last two weeks recording my CDs into this drive to use it as a music server.... I don't want to have to repartition and start over........

Thanks in advance for any help  :-(

---

### Post by talsemgeest on 2008-10-31
If you don't mind it mounting at startup, edit your fstab

```
gksudo gedit /etc/fstab
```

and find your drive. If it isn't there, take a look here for instructions: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---

### Post by murdison on 2008-11-01
Thanks for the help!!

OK... I've got the drive automounting on boot.

I've noticed that everytime I use SUDO, my terminal tells me: 

```
sudo: unable to resolve host MediaServer
```

What's that all about??


Thanks again, in advance!!!!

---

### Post by talsemgeest on 2008-11-01
Take a look here: [http://ubuntuforums.org/showthread.php?t=615579](http://ubuntuforums.org/showthread.php?t=615579) , see if that helps.

---

