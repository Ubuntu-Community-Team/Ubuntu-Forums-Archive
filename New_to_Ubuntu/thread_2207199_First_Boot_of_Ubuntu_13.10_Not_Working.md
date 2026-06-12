---
title: "First Boot of Ubuntu 13.10 Not Working"
date: 2014-02-22
forum: New to Ubuntu
---

### Post by Darren_Haynes on 2014-02-22
have been trying to get Ubuntu up and running in dual boot, this is  the first time I have tried to install linux. Everything was going well  with the install, the progress bar had reached the end of installing  files and then I got a black screen with a few lines of writing on it  that forced my laptop to shut down.   On booting I was taken to grub, where I have the option to boot in  Ubuntu and windows (and some other options), when booting Ubuntu I am  sent to a black screen with blinking cursor. I can type there, but  nothing else happens. Courtesy of some help I found out about, changing "quiet splash" to "nomodeset" and hitting ctrl-k via advanced settings for Ubuntu in grub. I  am now taken to a black screen with a lot of stuff going on line by  line and then the last line is:

  [INDENT]   [     7.471657] Adding 4041724k swap on /dev/sda7 Priority :-1   extents: 1 across :4041724k FS
 [/INDENT]  Underneath that line I am left with the blinking cursor again and nothing happens.
  Extra Details:
  
[LIST]
[*]I installed Ubuntu onto a partition
[*]I used a USB created with Linux/Live for install
[*]Using Ubuntu 13.10
[/LIST]
  Not sure if this detail is relevant but I noticed that Python 3 and  some other files were uninstalled after being installed when I watched  what files were being written during the progress bar on installation.  Just struck me as strange.


  Any ideas on what I can do to get things working?

---

### Post by Darren_Haynes on 2014-02-24
:sad::sad::sad:

---

