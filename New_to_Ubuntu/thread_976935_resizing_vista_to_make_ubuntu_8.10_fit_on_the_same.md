---
title: "resizing vista to make ubuntu 8.10 fit on the same HD"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by tysonh on 2008-11-09
I just download 8.10.  I put in the live cd and try to install it but I don't have any option to resize the partitions so I have room for ubuntu.  I've never had these problems with xp but I'm stuck with it for the time being.  My questtion is this.  Is there anything else I have to do before I put the live cd to dual boot with vista?

---

### Post by randy78 on 2008-11-09
Check here: [http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")

---

### Post by Zimmer on 2008-11-09
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

If you are dual booting Vista and Linux may I recommend EasyBCD.

Also, there are a few more tweaks about to con Vista into allowing you more space on the partition side of things. Turning off the pagefile and System Restore points for example. Vista still kept 70 plus gig for itself on my drive!! left me with about 30gb for Ubuntu and then 35 gb for a data partition, which is fine for now.

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by bumanie on 2008-11-09
Right click my computer; choose manage; then choose manage disks. Right click on the partition you want to alter (usually C:\) and from the drop downmenu, choose shrink. You should be use a slider to resize vista. Doing it this way usually achieves a more controlled reduction in the partition than letting vista do it itself. Before shrinking, defrag at least twice.

---

### Post by tysonh on 2008-11-09
sweet thanks for the help I got it all working now.

---

### Post by randy78 on 2008-11-09
Don't forget to mark the post as solved using the Thread Tools menu near the top of the page :D

---

