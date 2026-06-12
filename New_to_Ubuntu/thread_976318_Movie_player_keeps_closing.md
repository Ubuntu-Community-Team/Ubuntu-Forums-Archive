---
title: "Movie player keeps closing"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by SteelCore on 2008-11-09
Every time I try to open a file (audio or video) with Movie Player it opens for a second and then closes.  Using 8.10
Thanks

---

### Post by dracayr on 2008-11-09
open a terminal and open the video file with ```
totem /Path/to/file
``` post the output here. as an alternative, consider installing vlc

dracayr

---

### Post by SteelCore on 2008-11-09
here's the output
```

** (totem:13231): DEBUG: Init of Python module
** (totem:13231): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:13231): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:13231): DEBUG: Creating Python plugin instance
** (totem:13231): DEBUG: Init of Python module
** (totem:13231): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:13231): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:13231): DEBUG: Creating Python plugin instance
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 46 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

---

### Post by dracayr on 2008-11-09
add these lines to the /etc/X11/xorg.conf in the section "Device":```
Option "VideoRam" "65536"
Option "CacheLines" "1980"
``` you'll need root rights to do this, so edit it with this command:```
sudo gedit /etc/X11/xorg.conf
```. restart X: Ctrl+Alt+Backspace and log back in. then try again.

dracayr

---

### Post by SteelCore on 2008-11-09
Unfortunately, still the same.

---

### Post by dracayr on 2008-11-09
:( this seemed to work with everyone who had this bug. maybe you should try some other values for the options in xorg.conf. There are a few mentioned here: [https://launchpad.net/ubuntu/+source/totem/+bug/4229](https://launchpad.net/ubuntu/+source/totem/+bug/4229)

you can also try the option ```
Option "LinearAlloc" "16000"
``` in the device section. If you have compiz (Desktop effects) enabled, disable it and try again.

dracayr

---

### Post by SteelCore on 2008-11-09
Thank you for reminding me about Compiz. I actually disabled it from System>Preferences>Appearance and Movie Player is working properly now.
BTW do I need to remove ```

Option "VideoRam" "65536"
Option "CacheLines" "1980"
```
from xorg.conf

---

### Post by dracayr on 2008-11-09
Probably you don't *have to* remove it, but it's cleaner.

dracayr

---

