---
title: "[SOLVED] Empty xorg.conf file"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by mwalimu54 on 2008-09-16
Hello,  I'm new to ubuntu after ditching xp in a moment of intrepidity.  I am currently writing this post from a dell inspiron 1100 with a 82845g built in graphics card and running Feisty.  I have my graphics running with the generic Vesa driver at full resolution but my screen is very grainy and flickers.  I followed some threads to try to correct this but found my xorg.conf file is empty.  What can I do to correct this?  And yes, I have changed video memory to 8 MB and updated my bios to A32.

---

### Post by Separ on 2008-09-16
Just to confirm, can you post the output of ```
cat /etc/X11/xorg.conf
```

---

### Post by forger on 2008-09-16
You said you are using feisty, which is two releases older.
You could download and try ubuntu hardy 8.04.1 instead:
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

---

### Post by mwalimu54 on 2008-09-16
> **Separ said:**
> Just to confirm, can you post the output of ```
cat /etc/X11/xorg.conf
```

from root

"no such file or directory"

---

### Post by -Zeus- on 2008-09-16
whoa.  try tunning this.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mwalimu54 on 2008-09-16
> **forger said:**
> You said you are using feisty, which is two releases older.
You could download and try ubuntu hardy 8.04.1 instead:
[http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/)

I tried and so have others, but Hardy won't even run with the live cd on my inspiron.  the inspiron 1100 is a real lemon when it comes to compatibility with ubuntu

---

### Post by mwalimu54 on 2008-09-16
> **-Zeus- said:**
> whoa.  try tunning this.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

ran it and set resolution to 1024 x 768 only which is max default for this laptop. should i reboot or what next?

---

### Post by shoot2kill on 2008-09-16
also, if you are a new linux user, did you use a capital X in "X11" in the terminal..

as far as i knew, your system wouldnt boot or work properly if there wasnt an xorg.conf file, i may be wrong

---

### Post by drs305 on 2008-09-16
When you say your xorg.conf file is empty, are you trying to look at it from the livecd? If so, you have to mount your normal / folder first, and then open it. For instance:
```

sudo mount /dev/sda1 /mnt
gksu gedit /mnt/etc/X11/xorg.conf

```

If you want to mount it on something other than /mnt, make the mountpoint first.

This same principle applies to any system files you want to view or edit while running the livecd.

---

### Post by mwalimu54 on 2008-09-16
> **shoot2kill said:**
> also, if you are a new linux user, did you use a capital X in "X11" in the terminal..

as far as i knew, your system wouldnt boot or work properly if there wasnt an xorg.conf file, i may be wrong

GOTTIT!  So much for a newbie to learn such as a capital X. Now to make the appropriate changes.

---

