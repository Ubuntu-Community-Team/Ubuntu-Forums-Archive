---
title: "Porblems installing Codecs"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by eyesidol on 2008-06-07
im tying to install the codec package from this site:[http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml]("http://news.softpedia.com/news/How-to-Install-Multimedia-Codecs-in-Linux-39555.shtml") and i can do the first three command lines, but after that, the fourth says

andrew@andrew-desktop:~$ cp all-20061022/* /usr/local/lib/codecs/
cp: cannot stat `all-20061022/*': No such file or directory


and the fifth says

andrew@andrew-desktop:~$ chmod 755 /usr/local/lib/codecs/*
chmod: changing permissions of `/usr/local/lib/codecs/all-20061022': Operation not permitted
chmod: changing permissions of `/usr/local/lib/codecs/all-20061022.tar.bz2': Operation not permitted

sixth

andrew@andrew-desktop:~$ cp /usr/local/lib/codecs/* /usr/lib/win32/
cp: omitting directory `/usr/local/lib/codecs/all-20061022'
cp: cannot create regular file `/usr/lib/win32/all-20061022.tar.bz2': Permission denied

please help me with this, ive been at it for hours and cant get any of it to work.

---

### Post by halln on 2008-06-07
do this how to, instead, I think it's better to use medibuntu repo if you want multimedia codecs.[http://ubuntuforums.org/showthread.php?t=818449&highlight=medibuntu](http://ubuntuforums.org/showthread.php?t=818449&highlight=medibuntu)

---

### Post by Nepherte on 2008-06-07
As halln suggested, use the Medibuntu repository. It is a lot easier. For the actions you are trying to undertake, you need sudo privileges. Place sudo in front of every command.

---

### Post by avtolle on 2008-06-07
Add me to those suggesting you use the Medibuntu Repositories to add codecs.

---

### Post by Oldsoldier2003 on 2008-06-07
medibuntu is good but you can easily start the process by

```
sudo apt-get install ubuntu-restricted-extras
``` I've never really found a compelling reason to install the medibuntu repos to my sources.list

---

### Post by avtolle on 2008-06-07
Some of us became accustomed to using Medibuntu before restricted-extras was available. :-)

---

### Post by Happy_Man on 2008-06-07
Why not just use ```
sudo apt-get install gstreamer0.10-plugins-*
```?

---

### Post by halln on 2008-06-07
try this link aswell, very helpfull : [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by eyesidol on 2008-06-09
All very helpful, thanks

---

