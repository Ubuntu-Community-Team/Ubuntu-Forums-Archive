---
title: "restart Unity from console"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by Marchello_Lippi on 2013-09-01
Hi all, 

how do I restart Unity from console? Sometimes it just freezes, so I must restart pc...

---

### Post by deadflowr on 2013-09-01
Restart Unity or reboot system?
If wanting to restart unity I usually forego trying to restart unity from a terminal and instead kill X and restart through TTY1, or 2-6.
In a normal terminal you should just have to type unity and unity will start running.
To restart X press ctrl+ alt+ F1, or 2 and then a full screen terminal prompt will show. Enter your name and password.
Then enter
```
sudo service lightdm restart
```
This will stop and then start the X session again.
Mind you when you do this it'll move you back into the TTY7, and the full screen terminal will be in which ever one you picked (F1, or F2) will still be opened.
You can close the full screen terminal window by typing exit and then hit enter, which'll close that session.

Of course if this is happening alot, look over this to help diagnose the freeze problems
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by nns2006 on 2013-09-01
Are you using ubuntu 12.04? Recently I also had this experience see this [thread]("http://ubuntuforums.org/showthread.php?t=2170384"). Nothing was working, no terminal no Alt+F2-6 or Alt+REISUB. I installed Ubuntu 13.04 and it is fine up to now.

---

