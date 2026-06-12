---
title: "Installing driver from DVD file"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-08
I have Ubuntu 12.10 installe3d in dual boot so I can use windows to get online. One problem I have is that my Atheros ethernet isn't working. I found a possible solution but, with no internet access in Unbuntu, I could not use it directly.

What I was able to do is download the archive for the drivers and save that to my DVD. Now, I need to know how to install those drivers from the archive.

The name of the archive is: compat-wireless-2012-07-03-pc.tar.bz2

I'm still learning my way around the desktop but have found how to get to the terminal. Actual command usage is a bit "iffy" still.

Thanks!

---

### Post by ppjdee on 2013-04-08
Maybe this will help you.
[http://ubuntuforums.org/showthread.php?t=2088179](http://ubuntuforums.org/showthread.php?t=2088179)

---

### Post by alhefner on 2013-04-08
Good info ppjdee! However, I'm not sure how linux or Unbuntu designates drives and such so what would I replace ```
cd /media/USBTHUMB/
``` with? The name of the DVD disk itself is "install_stuff". In windoze, it's drive "D"... 

Like I said, this Linux stuff is 100% new to me.

---

### Post by ppjdee on 2013-04-08
prolly change the /usbthumb/ to cdrom, is my guess.. but you could move the file to the homefolder too.

---

### Post by alhefner on 2013-04-08
> **ppjdee said:**
> prolly change the /usbthumb/ to cdrom, is my guess.. but you could move the file to the homefolder too.

DOH! I seem to be an expert at making things much more difficult than they need to be!](*,) I'll give that a shot!

---

### Post by ppjdee on 2013-04-08
i do the same esp when its 4am and no sleep lol
anyways linux noob myself, but feel free to post questions maybe someone will have an answer.
goodluck

---

### Post by alhefner on 2013-04-08
OK, solved finally and am not using Ubuntu on the internet! Woohoo! Now, I gotta get WINE and get my Verizon wirele4ss running.

What I ended up doing was to use a windoze utility to uncompress the bz2 into it's own directory on the host direcftory of the file system. THEN, I started Ubuntu and copied it to my home directory. The file was still a .tar file and I could uncompress it using the Linux system into yet another directory...

Once all that was done, the rest went according to the initial instructions pretty well.

---

### Post by ppjdee on 2013-04-08
Glad to hear you got it working!

---

