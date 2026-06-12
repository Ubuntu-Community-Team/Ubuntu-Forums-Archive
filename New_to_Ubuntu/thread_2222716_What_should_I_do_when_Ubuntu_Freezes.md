---
title: "What should I do when Ubuntu Freezes?"
date: 2014-05-07
forum: New to Ubuntu
---

### Post by christo3 on 2014-05-07
Have been using Ubuntu for 5 years now. 
And I have been thinking about how to troubleshoot Ubuntu when a program hangs or the system freezes. 
Here is a useful link to some quick solutions [http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717](http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717)
I suggest writing these down somewhere or sticky-note them to your desk
Please add some other useful commands and links

---

### Post by olliemonster on 2014-05-14
Another useful thing if you can use the command line is ctrl alt f1/f2/f3/f4/f5/f6 this will get you into a tty console so you can either restart lightdm with  ```
sudo service lightdm resart
``` or ```
sudo shutdown -r now
``` to restart now

---

### Post by jmeeter on 2014-05-14
**When a single program stops working:**

When a program window stops responding, you can usually stop it by clicking the X-shaped close button at the top left of the window. That will generally result in a dialog box saying that the program is not responding (but you already knew that) and presenting you with the option to kill the program or to continue to wait for it to respond.

Sometimes this does not work as expected. If you can't close a window by normal means, you can hit Alt+F2, type xkill, and press Enter. Your mouse cursor will then turn into an X. Hover over the offending window and left-click to kill it. Right clicking will cancel and return your mouse to normal.

If your program is running from a terminal, on the other hand, you can usually halt it with Ctrl+C. If not, [find the name and process ID of its command]("http://askubuntu.com/questions/180336/how-to-find-the-process-id-pid-of-a-running-terminal-program"), and end it with kill [process ID here]. If that fails despite waiting a few seconds, try sending a SIGHUP: kill -HUP [process ID here]. If all else fails, as a last resort send SIGKILL (-9): kill -9 [process ID here]. Note that you should only use SIGKILL as a last resort, because the process will be terminated immediately with no opportunity for cleanup.

**When the mouse stops working:**

If the keyboard still works, press Alt+F2 and run gnome-terminal (or, if these fail to launch, press Alt+Ctrl+F1 and login with your username and password). From there you can troubleshoot things. I'm not going to get into mouse troubleshooting here, as I haven't researched it. If you just want to try restarting the GUI, run sudo service lightdm restart. This should bring down the GUI, which will then attempt to respawn, bringing you back to the login screen.
When everything, keys and mouse and all, stop working:

First try the Magic SysReq method outlined in [this answer]("http://askubuntu.com/questions/4408/what-should-i-do-when-ubuntu-freezes/36717#36717"). If that doesn't work, press the Reset button on the computer case. If even that doesn't work, you'll just have to power-cycle the machine.

***May you never reach this point.***

[[source]]("http://askubuntu.com/a/4412/280643")

---

