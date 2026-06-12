---
title: "[SOLVED] xsane broken"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-10-29
I just installed Intrepid and my xsane worked fine. However, like I did in Hardy (Without a problem) I removed all the sane/xsane and compiled the newest versions of both and installed those. Unlike in Hardy though, this time they do not work. The problem is even after I ran ```
sudo make uninstall
``` and reinstalled the sane and xsane utils from the repos, now even they no longer work/detect my scanner (which they did before). Can anyone think of a reason that a compiled version of sane and xsane would work on hardy but not intrepid AND, more importantly, can anyone think of a way to get the repo versions working again.

Thanks

---

### Post by JohnGalt131 on 2008-10-29
Sorry, got it working! Somehow or other, hplip got removed. Once reinstalled everything works.

---

### Post by leemckusic on 2010-04-11
I have a machine running the 8.04 (Hardy?) Ubuntu and xsane (scanimage)
works fine.

The same USB scanner plugged into a 9.10 (Intrepid?) Ubuntu machine fails to run Xsane with various "no scanner found" errors. scanimage -L does show the scanner but it does not figure out the name of the scanner.

The application (xsane or scanimage) has a permissions problem and running the command with sudo causes the scanner to work again.

I do my scanning with a command line. The "sudo" bypasses the permission problem and gets things working:

sudo scanimage --resolution 400 | pnmtojpeg>outputfilename.jpeg
;
eog outputfilename.jpeg

[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

