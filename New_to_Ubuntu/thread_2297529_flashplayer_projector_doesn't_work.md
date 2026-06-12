---
title: "flashplayer projector doesn't work"
date: 2015-10-04
forum: New to Ubuntu
---

### Post by flex567 on 2015-10-04
I tried to run Flash player projector for linux([https://www.adobe.com/support/flashplayer/debug_downloads.html](https://www.adobe.com/support/flashplayer/debug_downloads.html)) and I got the  error: 

```

./flashplayer ./flashplayer: error while loading shared libraries: libssl3.so: cannot open shared object file: No such file or directory

```

Is there a way to fix this?

---

### Post by sandyd on 2015-10-04
Try
```

sudo apt-get install libnss3:i386
```

---

### Post by flex567 on 2015-10-05
> [COLOR=#000000]Try[/COLOR]
[COLOR=#000000]Code:
[/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install libnss3:i386[/FONT][/COLOR]

It still doesn't work, now I get this error:
```

./flashplayer: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```

---

### Post by flex567 on 2015-10-05
if there is no solution how can I delete the installed package?

---

### Post by sandyd on 2015-10-05
Just delete the folder you extracted.

Also, there is a solution.

Each time there is a missing library, do this:

Go to [http://packages.ubuntu.com/](http://packages.ubuntu.com/), where it says "Search the contents of packages", enter in the library name. In this case, it is "libgtk-x11-2.0.so.0"

After changing to the correct ubuntu distribution, that brings me to a page where I can see that libgtk-x11-2.0.so.0 is in the package "libgtk2.0-0". The fact that there are two packages indicates that there is a i386 (x86) version of the package, and a amd64 (x64) version of the package. Flashplayer projector seems to be x86, so we add i386 to the package name with a colon inbetween i386 and the package name. Now we have "libgtk2.0-0:i386". Install that with apt-get and repeat for any other missing libraries.

---

### Post by flex567 on 2015-10-06
I have installed the missing library and now the program runs but it closes after one second with this error:

```
(flashplayer:3602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(flashplayer:3602): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module"
Vector smash protection is enabled.


(flashplayer:3602): GLib-GObject-WARNING **: instance with invalid (NULL) class pointer


(flashplayer:3602): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed



```

---

### Post by flex567 on 2015-10-06
[COLOR=#000000]if there is no solution how can I delete the installed packages?[/COLOR]

---

### Post by sandyd on 2015-10-06
Just replace "install" in the apt-get command with "remove"

i.e.
```
sudo apt-get remove libgtk2.0-0:i386

```

---

### Post by flex567 on 2015-10-07
```
sudo apt-get remove libgtk-x11-2.0.so.0:i386[sudo] password for seba: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtk-x11-2.0.so.0
E: Couldn't find any package by regex 'libgtk-x11-2.0.so.0'
```

??

---

### Post by flex567 on 2015-10-07
When I try to install I get:
```
seba@seba-H81-D3:~$ sudo apt-get install libgtk-x11-2.0.so.0:i386[sudo] password for seba: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgtk-x11-2.0.so.0
E: Couldn't find any package by regex 'libgtk-x11-2.0.so.0'



```

---

### Post by Geoffrey_Arndt on 2015-10-07
Need to check your input.    Every character & space matters, and must be 100%.   That's why I like cut & paste - - eliminates user error.

---

### Post by flex567 on 2015-10-07
What is there to check I used this post, just replaced remove with install ?

> **sandyd said:**
> Just replace "install" in the apt-get command with "remove"

i.e.
```
sudo apt-get remove libgtk-x11-2.0.so.0:i386

```

---

### Post by sandyd on 2015-10-07
There was a typo in the example - fixed

---

