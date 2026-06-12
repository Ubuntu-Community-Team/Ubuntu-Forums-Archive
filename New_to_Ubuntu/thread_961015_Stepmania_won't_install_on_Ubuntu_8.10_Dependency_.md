---
title: "Stepmania won't install on Ubuntu 8.10 Dependency error"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by spajix on 2008-10-27
I've tried with the .debs from stepmania's site and for getdeb.net
For stepmania you have to install stapmania-data and stepmania
stapmania-data works fine but stapmania gives me
[CODE] Error: Dependency is not satisfiable: libavcodec1d[/CODE=]
Any idea's on how I can fix this?

---

### Post by spiderbatdad on 2008-10-27
does not appear to be in universe yet...maybe in backports...or here:
[http://packages.ubuntu.com/gutsy/libs/libavcodec1d](http://packages.ubuntu.com/gutsy/libs/libavcodec1d)

---

### Post by spajix on 2008-10-27
I tried installing through that way but I keep rinning into dependency issue's... I have to install this to install this to install that... 
When will this be fixed? When Ubuntu 8.10 is out of beta?
I guess I'll have to wait
Cause it's saying I need to install something I have installed...

---

### Post by Crafty Kisses on 2008-10-27
What are the results of this command?
```
glxinfo
```

---

### Post by spiderbatdad on 2008-10-27
wow crazy game...I was able to run it like this:
I downloaded the source here:
[http://sourceforge.net/project/showfiles.php?group_id=37892&package_id=30318&release_id=565571](http://sourceforge.net/project/showfiles.php?group_id=37892&package_id=30318&release_id=565571)
Get the tar.gz
I saved it to my desktop, then right clicked the package and selected 'extract here.'
Next ran in a terminal:```
cd Desktop/Step (just hit the tab key to complete the file name.)
sudo apt-get install libpng
./stepmania
```Bingo should start.

---

### Post by spajix on 2008-10-28
Thanks I finaly got it working

---

