---
title: "Python Newbie"
date: 2005-11-21
forum: Programming Talk
---

### Post by chronusdark on 2005-11-21
im trying to make a python script that when i run it it will replace some files and then restart X but i dont know how to execute external programs/scripts could someone tell me how to do this?

also i need to know how to restart x from a command line

thanks in advance

---

### Post by Burke on 2005-11-21
I think you can type '/etc/init.d/gdm restart' to accomplish this. I have too much stuff open to try it right now, but I think it'll work.  As for the python part, I'm not sure how so run a shell command, but I think you know. Could you post that part?  I'm interested :)

---

### Post by Burke on 2005-11-21
I reread your post and realized you said you didn't know how to do the Python part, so I googled it:

import os
stdout, stdin = os.popen4("/etc/init.d/gdm restart")

I'm going to try it now.  If I don't edit this post within a minute, it worked :)

EDIT:  nope, it didn't work.  The python code works, but the shell command doesn't to anything.  I'll let you know if I find out how to do this.

---

### Post by Roptaty on 2005-11-22
[QUOTE=Burke]I reread your post and realized you said you didn't know how to do the Python part, so I googled it:

import os
stdout, stdin = os.popen4("/etc/init.d/gdm restart")

I'm going to try it now.  If I don't edit this post within a minute, it worked :)

EDIT:  nope, it didn't work.  The python code works, but the shell command doesn't to anything.  I'll let you know if I find out how to do this.[/QUOTE]

You need to use sudo to restart gdm.

---

### Post by Burke on 2005-11-22
haha,  yeah, that definitely works... I don't know why I didn't get that :)

So here it is:

import os
stdout, stdin = os.popen4("gksu /etc/init.d/gdm restart")

...and that should prompt you for a password to restart X.

---

### Post by chronusdark on 2005-11-22
sweet


i gotta do dishes or my g/f will kill me but i will try that out today

thanks alot

---

