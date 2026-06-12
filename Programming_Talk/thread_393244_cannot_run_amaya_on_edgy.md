---
title: "cannot run amaya on edgy"
date: 2007-03-25
forum: Programming Talk
---

### Post by weldan on 2007-03-25
root@dan-desktop:/home/dan# amaya
02:17:52 AM: Deleted stale lock file '/root/.amaya-root'.

(amaya:7736): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 5361 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

root@dan-desktop:/WWW/files# uname -a
Linux dan-desktop 2.6.17-11-generic #2 SMP Thu Feb 1 19:52:28 UTC 2007 i686 GNU/Linux


anyone please help me.. :(

---

### Post by lptr on 2007-04-18
Same here under Feisty.

```
$ /usr/lib/amaya/wx/bin/amaya
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
16:30:50: Deleted stale lock file '/home/roberts/.amaya-roberts'.

(amaya:8495): Gtk-CRITICAL **: gtk_widget_set_colormap: assertion `!GTK_WIDGET_REALIZED (widget)' failed
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 7741 error_code 8 request_code 142 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by puccaso on 2007-06-11
did u find a fix for this?  i got the same error with totem.

---

### Post by coolglobal on 2007-06-23
I have just experienced the same bug. Fixed by completely removing Amaya then downloading and installing the latest version, see below.

UPDATE
I installed the latest build from the website, 9.54, and it now opens.
[http://www.w3.org/Amaya/User/BinDist.html](http://www.w3.org/Amaya/User/BinDist.html)

---

