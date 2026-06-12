---
title: "automounting cd/dvd image"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by vocalstud69 on 2008-07-16
Is there a way to automount a cd/dvd *.iso without having to load in the cli the code for it?  Like, right click on the file and click 'Mount' kind of easy? I was thinking of a shell script, but I don't think that would work.  I actually don't care, but my sister has issues with this because she can't remember the commands because I told her that she could back up all he movies into an .iso image and mount them on linux, which is the con I used to get her to stop using Vista.  Anybody have similar annoyances, and did anybody figure out a good way to do it.  

My sister actually wants a choice in the menu that shows up on Ubuntu 8.04 when you right click on a file, one of the options is 'Mount CD/DVD Image', and it would automount to a folder.  

Help!

---

### Post by nowshining on 2008-07-16
a script should work :) and in nautilus u can add it to the scripts folder..I forgot where it is, i use kubuntu.

---

### Post by vocalstud69 on 2008-07-16
Yeah, but I'm an idiot and don't remember anything about shell scripts.  Know where I can find a tutorial on it?

Also, would that give me the option to 'Mount CD/DVD Image' in the right click menu?

---

### Post by nowshining on 2008-07-16
it should be a right menu - scripts - and as for Mound CD/DVD image thing, it will show as whatevre you named it..

for bash just add this @ the top:

```
 #!/bin/bash 
```

then add the command like u do in the terminal for a  basic script.

---

### Post by vocalstud69 on 2008-07-16
Thanks.  I'll try it when I get home tonight, since I'm on a windows box at work.

---

### Post by bodhi.zazen on 2008-07-16
Just put an entry in fstab :

```
/path_to/file.iso 	/media/mount_point  udf,iso9660  user,auto,loop 	0	0
```

---

### Post by imon9 on 2008-07-16
use this program 
[http://sourceforge.net/projects/acetoneiso2/](http://sourceforge.net/projects/acetoneiso2/)

just select the iso and it mounts it automatically like a cdrom drive (virtual cdrom)

---

