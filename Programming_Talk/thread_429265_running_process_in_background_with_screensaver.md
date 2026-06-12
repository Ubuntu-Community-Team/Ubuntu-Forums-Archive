---
title: "running process in background with screensaver"
date: 2007-05-01
forum: Programming Talk
---

### Post by hardyn on 2007-05-01
does this exist, or where might a guide be found to run a process in the background with a screen saver?

for projects like folding@home or seti@home, without Linux screen savers, can i execute files at the start of a screen saver, and kill them when the screen saver session is finished?  does this sort of thing already exist? or how much work it is to write a screen saver? i have a little C experience.

thanks.

---

### Post by schleich on 2007-05-10
I would also like to know if this is possible.  I'm pretty bad at remembering to start the process when I get up from the computer.

---

### Post by vinicios.ec on 2011-06-26
hello fellows,
I was trying to get some information about that too.
Like launch a transmission torrent downloader when the screensaver starts to run, and ends the transmission when scrensavers gone.
thinking with my self, I consider to start some sh script to verify the gnome-screesaver process. ps -e | grep "screensaver", and then just call transmission. when the process is overed, then just kill the transmission. pretty simple, but maybe will not work fine.
some good idea?

---

### Post by juancarlospaco on 2011-06-27
[http://ubuntuforums.org/showpost.php?p=10983495&postcount=5](http://ubuntuforums.org/showpost.php?p=10983495&postcount=5)

---

