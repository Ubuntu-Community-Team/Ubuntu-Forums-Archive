---
title: "Help me!!! How to install this app??"
date: 2012-09-21
forum: New to Ubuntu
---

### Post by RAJASD on 2012-09-21
i want to install this applet

[http://cricscoreapplet.sourceforge.net/](http://cricscoreapplet.sourceforge.net/)

it says 'unpack the source'
what should i do??

Thank you

---

### Post by Deepak A on 2012-09-21
Open a terminal:
change to download directory where you downloaded cricscore-1.1.0.5.tar.gz

$cd /path/to/the/download/directory
then do,

$tar -xzf cricscore-1.1.0.5.tar.gz 

change to extracted directory using,
$cd cricscore-1.1.0.5

run a command,
$make install

then log out and login back again.

---

### Post by RAJASD on 2012-09-21
> **Deepak A said:**
> Open a terminal:
change to download directory where you downloaded cricscore-1.1.0.5.tar.gz

$cd /path/to/the/download/directory
then do,

$tar -xzf cricscore-1.1.0.5.tar.gz 

change to extracted directory using,
$cd cricscore-1.1.0.5

run a command,
$make install

then log out and login back again.

i dont know how to change the download directory..pls tell me how..i am new to ubuntu

thanks

---

### Post by MElawe on 2012-09-21
Open terminal and use the cd command. For example, if you want to go to desktop: ```
cd Desktop
```
Or a folder in your music folder ```
cd Home/Music/folderName
```.

---

### Post by 3rdalbum on 2012-09-21
I don't think it will work.

First reason: It was last updated in 2010. Linux changes a lot internally in two years and the program hasn't been updated to work with the changes. It might not even compile on today's Linux distributions.

Second reason: Presumably as a result of being from 2010, it is a Gnome panel applet; Ubuntu's current desktop environment was written in 2011 and does not support the old Gnome applets. Gnome 3 was written around the same time and doesn't support the old Gnome applets.

Third reason: There's no guarantees that the data source the program is getting its information from, still exists or is still the same in 2012. The website that the program reads may deliver its information in a different way that the program doesn't understand.

Even if it does work, it's probably not worth the bother of installing all the development libraries and compiling the software. The developer really should have released a proper Ubuntu package for the software so it would be easy to install.

Sorry for the pessimistic viewpoint, but IMHO it's rarely worthwhile to compile a piece of software that's been out of development for so long.

---

