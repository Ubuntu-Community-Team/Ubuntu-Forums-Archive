---
title: "Hiding a running application?"
date: 2012-06-09
forum: New to Ubuntu
---

### Post by ezzy25 on 2012-06-09
How do I hide a running application so that it does not appear in the launcher or appear when I alt-tab through the applications I have open?

I have a simple one line script set to run at startup that simply launches a java application.  The program is meant to just run in the background, so it is really annoying to have it show up when I alt-tab to switch applications.  There is an option to hide it by right clicking on the notification icon, but I was wondering if there were a way to automatically hide it through that startup script.

Ubuntu 12.04

---

### Post by numand on 2012-06-09
@ezzy25, 

[http://askubuntu.com/questions/96011/running-commands-on-boot-in-11-10](http://askubuntu.com/questions/96011/running-commands-on-boot-in-11-10)
[http://askubuntu.com/questions/89518/upstart-script-and-start-stop-daemon](http://askubuntu.com/questions/89518/upstart-script-and-start-stop-daemon)
[http://manpages.ubuntu.com/manpages/karmic/man8/start-stop-daemon.8.html](http://manpages.ubuntu.com/manpages/karmic/man8/start-stop-daemon.8.html)

I hope these links will help you.

---

### Post by ezzy25 on 2012-06-09
Thanks for the response.  That seems to be more complicated that what I was trying to accomplish though... I guess all I really need is a way to hide an already running application.  Any thoughts?

---

### Post by numand on 2012-06-10
You are wellcome @ezzy25. You can try to add "&" at the and of the command: ```
foo &
```.

---

### Post by zombifier25 on 2012-06-10
If you are using Unity 3D (Compiz), install ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
The launch ccsm, go to section Windows Management, enable Windows Rules. Then choose it, and add this line into "Skip Taskbar" and "Skip Pager":
```
title=nameofwindow
```
Replace nameofwindow with the title of the window you want.

---

### Post by ezzy25 on 2012-06-11
Thanks guys!  I was able to use Compiz to hide the application from the launcher and app switcher. I could not figure out how to start the application minimized, but I was able to use a simple devilspie script to hide the window once it is opened.  Also, the & symbol was indeed required after the line to launch the application so that the next lines in the script to run the devilspie code could be executed.

---

