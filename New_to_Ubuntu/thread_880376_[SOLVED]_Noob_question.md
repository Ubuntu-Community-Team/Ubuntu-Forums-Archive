---
title: "[SOLVED] Noob question"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by sithpigeon on 2008-08-04
alright this is going to sound really bad but how do you save a list of commands in terminal to a file and then execute them all, one after another. so like if i wanted to right a file that opens up firefox, terminal, and gedit for righting programs in c++.

---

### Post by Linux_Man on 2008-08-04
Well you could type them all in and add a & at the end, or you could create a shell script that automatically executes them.


For example typed in 

firefox & gedit &


That would open up both Firefox and gedit

---

### Post by sithpigeon on 2008-08-04
i know but I'm not sure how to create the shell script

---

### Post by noobuntu35 on 2008-08-04
> **sithpigeon said:**
> alright this is going to sound really bad but how do you save a list of commands in terminal to a file and then execute them all, one after another. so like if i wanted to right a file that opens up firefox, terminal, and gedit for righting programs in c++.

can you be more specific as to what you want to execute I.e are you looking for apt-get install commands linked commands??? or are you suggesting a .batch style command (DOS ref)...

---

### Post by Linux_Man on 2008-08-04
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)


Is a good tutorial 

But I belive you can just type in 


```
#! /bin/bash
gedit & firefox &
```

And save it as like somescript.sh 

then do chmod +rwx somescript.sh

then you can execute it with ./somescript

But that link has a lot more info

---

### Post by sithpigeon on 2008-08-04
Will look at Linux_Man's link.

---

### Post by noobuntu35 on 2008-08-04
> **Linux_Man said:**
> [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)


Is a good tutorial 

But I belive you can just type in 


```
#! /bin/bash
gedit & firefox &
```

And save it as like somescript.sh 

then do chmod +rwx somescript.sh

then you can execute it with ./somescript

But that link has a lot more info

if you add a  v in the +rwx command line you can see the output of the file as it is installed, also it's a double && here is an example of such a command
john@ubuntu:~$ sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install libdvdcss2 w32codecs

I can't remember what program this was now... also check the Debian sites for help. getdeb.net is an awesome site

EDIT: the site is for amarok a multimedia music player. medibuntu is the host site this was the visualizer lib installer

---

### Post by sithpigeon on 2008-08-04
ok so i tried noobuntu's idea and when I try to change the wallpaper like this```

#! /bin/bash
gnome-appearance-properties - /home/adam/Pictures/.a/untitled\ folder\ 19/wallpaper212.jpg
```
i get this error```

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

---

### Post by noobuntu35 on 2008-08-04
> **sithpigeon said:**
> ok so i tried noobuntu's idea and when I try to change the wallpaper like this```

#! /bin/bash
gnome-appearance-properties - /home/adam/Pictures/.a/untitled\ folder\ 19/wallpaper212.jpg
```
i get this error```

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

so lets check suggestions for the symptoms suggested I.E what is Bonobo? or do you have a conflicting gnome/kde manager? I'll search the second.

---

### Post by sithpigeon on 2008-08-04
that was dumb. it was just cause I was using sudo and it was executing it as root.

---

