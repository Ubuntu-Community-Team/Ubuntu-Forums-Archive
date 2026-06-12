---
title: "Shutdown problem"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by sharks on 2008-10-11
Just installed Gutsy. All works fine but when i try to shutdown , it stops at very end with a screen(nothing in that). How to solve it?

---

### Post by sharks on 2008-10-11
And also at the start, i cant see the ubuntu logo(loadin) . Instead it shows some text .

---

### Post by sharks on 2008-10-11
bump

---

### Post by unutbu on 2008-10-11
This does not work for all machines, but perhaps it will work for you.
If it does not work, it is not hard to undo the changes.

Try 
[list=1]
[*] 
```
gksu gedit /etc/modules
```
Add 'apm' to the bottom of the file. Save.

[*]Create the file /etc/modprobe.d/power:
```
gksu gedit /etc/modprobe.d/power
```
Add the line
```
options apm power_off=1 realmode_power_off=1
```
Save and quit.

[*]Now try booting again, but this time with kernel option "apm=on". (See [http://ubuntuforums.org/showpost.php?p=5586563&postcount=4](http://ubuntuforums.org/showpost.php?p=5586563&postcount=4) for info on how to boot with a kernel option.)
[/list]

This information comes from here: [http://ubuntuforums.org/showthread.php?t=237264](http://ubuntuforums.org/showthread.php?t=237264)

---

### Post by sharks on 2008-10-12
problem is still there..............

---

### Post by bumanie on 2008-10-12
Does it shutdown correctly by using command > sudo shutdown -h now

---

