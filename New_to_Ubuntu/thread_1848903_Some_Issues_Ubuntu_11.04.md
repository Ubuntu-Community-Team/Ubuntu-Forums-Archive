---
title: "Some Issues Ubuntu 11.04"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by User2011 on 2011-09-23
[FONT=Arial][SIZE=2]Hey there!!

I've just installed Ubuntu 11.04 on my pc desktop computer & I'm loving all of ubuntu's features and really thinking of totally switching to Ubuntu instead of using windows again. But the only problem I seem to be having with Ubuntu 11.04 is that my desktop is really classic, it only has a black bar on the bottom and on top, no icons on the left and I noticed the computer was very slow so I thought I might have to update Ubuntu but whenever I open the Update Manager, a error window pops up saying[/SIZE][/FONT] [SIZE=2]*NOT ALL UPDATES CAN BE INSTALLED - RUN A PARTIAL UPGRADE, TO INSTALL AS MANY UPDATES AS POSSIBLE*[/SIZE] and when I do so it doesn't work either, and not even the SYNAPTIC PACKAGE MANAGER works as well because every time I try to open it, I recieve an error message telling me to **manually run 'sudo dpkg -- configure-a' correct the problem**

Can anybody please help me? I really liked Ubuntu and I really want to start using it, but I will not be able to become an Ubuntu user with all these issues accuring... please help me! thank you...

---

### Post by Krytarik on 2011-09-23
How about this, already tried?:
> **User2011 said:**
> **manually run 'sudo dpkg -- configure-a' correct the problem**
Therefore, open the Terminal and run:
```
sudo dpkg --configure -a
```Hope it helps!

---

### Post by User2011 on 2011-09-23
[FONT=Tahoma][SIZE=2]Thank you very much! It did help! But its still not working. When I open the command and type the code in, I receive a note with my username, telling me to type in my password and when I do so, the command just freeze's! Therefore disabling me to type in my usernames password. [/SIZE][/FONT]

---

### Post by nothingspecial on 2011-09-23
You don't see your password when you type it.

Just type it and press enter.

---

