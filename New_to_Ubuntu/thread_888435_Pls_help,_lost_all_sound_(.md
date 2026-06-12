---
title: "Pls help, lost all sound :("
date: 2008-08-13
forum: New to Ubuntu
---

### Post by rhenium3 on 2008-08-13
I tried to do this: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Even though my sound worked ok.  Now all my sound is gone. Can someone help me copy the back up files back to their correct position?

Thanks

---

### Post by kpkeerthi on 2008-08-13
Try 
```
rm ~/.asoundrc
```

Reboot and then type **alsamixer** in a terminal and adjust the channel volumes.

---

### Post by rhenium3 on 2008-08-13
> **kpkeerthi said:**
> Try 
```
rm ~/.asoundrc
```

Reboot and then type **alsamixer** in a terminal and adjust the channel volumes.

You are a god, a bow down to you, THANK YOU SO MUCH!!!!

(I admit i was this** close to wanting windows)

Thank you again :)

---

### Post by kpkeerthi on 2008-08-13
You are welcome :)

---

### Post by Nepherte on 2008-08-13
Just mentioning that there are complete reversal instructions under Appendix C of the tutorial:
```
$ sudo apt-get install flashplugin-nonfree/hardy libsdl1.2debian-alsa
$ sudo rm ~/.asoundrc* /etc/asound.conf ~/.libao ~/.pulse/daemon.conf ~/.pulse/default.pa
$ sudo cp ~/pulse-backup/asound.conf /etc/
$ cp ~/pulse-backup/.asoundrc* ~/
```
If you got it working again, I would keep it that way.

---

