---
title: "libhildon-1-dev - develop hildon ui program"
date: 2009-08-07
forum: Programming Talk
---

### Post by weelaner on 2009-08-07
Hi,

i program on my eeepc (eeebuntu 8.10) a little "musicbox". Now i came to the point where I start developing the ui. Because of the small screen of my eeepc I choose hildon on top of gtk to program the ui. 
I am new in ui programming. I use eclipse(cdt) for programming and install the hildon-desktop parallel to the gnome desktop and it is working. 
Then I installed the libhildon-1-dev package from the repository ( and about 50 MByte dependencies ). 
When I now try the hello World example from maemo.org and bind my program to libhildon-1 there are some important functions missing. 
For example the **hildon_init_gtk(...)** function is missing. A hildon Button can`t be created too. 

Can someone here help me to solve this issue? Or is it impossible to develop hildon program directly under ubuntu?
If this forum is the wrong place for my post, please lead me to the right place. :-)

Thanks a lot...
weelaner

---

### Post by weelaner on 2009-08-07
Hi again,

i tested now the sample on 

[http://wiki.maemo.org/Documentation/Maemo_5_Developer_Guide/Application_Development/Getting_started](http://wiki.maemo.org/Documentation/Maemo_5_Developer_Guide/Application_Development/Getting_started)

without eclipse to be sure, I've made no misconfiguration. The output is the same. :confused:

with 
```
gcc base.c `pkg-config hildon-1 --cflags --libs` -o base
```
i get this error
```

/tmp/cc2vE349.o: In function`main`:
base.c:(.text+0x1c): undefined reference to `hildon_gtk_init`
collect2: ld returned 1 exit status

```
On my system are installed:
```

ii libhildon-1-0    2.0.1-1ubuntu6 Hildon libraries
ii libhildon-1-dev  2.0.1-1ubuntu6 Hildon libraries development files

```

Thanks
weelaner

---

### Post by weelaner on 2009-08-07
Hi,

I solved this issue by myself. The version of hildon in ubuntu 8.10 is 2.0.1. I looked to the older API references on maemo.org and there are lesser functionality inside this version. 
The current version of hildon is 2.1.x and the examples I used are for that version.

weelaner

---

