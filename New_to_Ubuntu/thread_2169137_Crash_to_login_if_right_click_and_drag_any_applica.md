---
title: "Crash to login if right click and drag any application window"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by whitecardamom on 2013-08-20
[COLOR=#0000cd]Hi,  I have a fresh install of ubuntu 12.4 64bit and everytime I right click and drag any application window on the desktop, the OS shuts off with a brief error message and sends me back to login screen.  Please let me know if I need more info or if someone has found a thread with a fix for this.  I am new so the learning curve is massive for me.  Thanks for your support! [/COLOR][COLOR=#0000cd] I hope I have the correct log file that might provide some info on the crash.  [/COLOR][COLOR=#0000cd]Below is the apport.log file for crashes:[/COLOR]

ERROR: apport (pid 23701) Tue Aug 20 13:27:10 2013: called for pid 1907, signal 6
ERROR: apport (pid 23701) Tue Aug 20 13:27:10 2013: executable: /usr/bin/Xorg (command line "/usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch -background none")
ERROR: apport (pid 23701) Tue Aug 20 13:27:11 2013: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 23701) Tue Aug 20 13:27:28 2013: wrote report /var/crash/_usr_bin_Xorg.0.crash
ERROR: apport (pid 24813) Tue Aug 20 13:30:12 2013: called for pid 23717, signal 6
ERROR: apport (pid 24813) Tue Aug 20 13:30:12 2013: executable: /usr/bin/Xorg (command line "/usr/bin/X :0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch")
ERROR: apport (pid 24813) Tue Aug 20 13:30:12 2013: is_closing_session(): no DBUS_SESSION_BUS_ADDRESS in environment
ERROR: apport (pid 24813) Tue Aug 20 13:30:17 2013: wrote report /var/crash/_usr_bin_Xorg.0.crash

----------------info----------------
[TABLE]
[TR]
[TD="class: field"]Processor[/TD]
[TD="class: value"]4x AMD Phenom(tm) II X4 955 Processor[/TD]
[/TR]
[TR]
[TD="class: field"]Memory[/TD]
[TD="class: value"]12267MB (3699MB used)[/TD]
[/TR]
[TR]
[TD="class: field"]Operating System[/TD]
[TD="class: value"]Ubuntu 12.04.2 LTS[/TD]
[/TR]
[/TABLE]
Graphics card        Nvidia Geforce GTX 660 2GB Memory
------------------------------------

---

