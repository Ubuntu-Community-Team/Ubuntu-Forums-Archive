---
title: "&quot;system restore&quot;"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by NaF on 2008-05-21
ref: [http://ubuntuforums.org/showthread.php?t=801143&page=2](http://ubuntuforums.org/showthread.php?t=801143&page=2)
I tried to get my ATI card working with two monitors, and ended doing... something wrong that resulted in a flickering 800x600 max resolution. Can I roll back to the drivers installed with ubuntu to begin with, in any way?

---

### Post by MaindotC on 2008-05-21
You need to edit xorg.conf.  If you go to the /etc/X11 directory you'll see different xorg.conf files numbered in descending order (1 being the most recent change in your xorg.conf, larger numbers approaching your first configuration).  Just move one of the numbered files to xorg.conf.

Try this method of copying the file, making the changes you need, then moving it back so it is referenced as xorg.conf:


```

cp xorg.conf xorg.conf.backup

```
Here's a backup just in case something goes awry.```

cp xorg.conf.1 xorg.conf

```
Edit the xorg.conf.1 file using nano as you wish.
```

mv xorg.conf.edit xorg.conf

```
This may give you an error if it will not let you replace xorg.conf with the file you edited. If it does allow you, restart your x-server or from the recovery console you can reboot.

---

### Post by NaF on 2008-05-21
> **strAlan said:**
> You need to edit xorg.conf.  If you go to the /etc/X11 directory you'll see different xorg.conf files numbered in descending order (1 being the most recent change in your xorg.conf, larger numbers approaching your first configuration).  Just move one of the numbered files to xorg.conf.


Ok, I didn't really understand what you said beyond this ;) But I just 
```

cd /etc/X11/
ls

```
and copied the content from:
```

gedit xorg.conf.[highestnumber]

```

and just Copy/pasted the content of that into the 
```

sudo gedit xorg.conf

```
When I Ctrl Alt Backspaced, it restarted and loaded up and said it had defaulted to low graphic mode? :confused:

---

### Post by MaindotC on 2008-05-21
You may want to just try going to System -> Administration -> Screens & Graphics and selecting the correct external monitor.  Do you have that option in your menu?

---

### Post by NaF on 2008-05-22
> **strAlan said:**
> You may want to just try going to System -> Administration -> Screens & Graphics and selecting the correct external monitor.  Do you have that option in your menu?

No when I go into there - I just have the options of two monitors both 19" (nothing other than the size to identify them), but no matter which one I select, nothing changes. :confused:

---

### Post by MaindotC on 2008-05-22
Oh I remember in Hardy it was removed from the menu for some reason.  Try this:
```

gksu displayconfig-gtk

```

---

