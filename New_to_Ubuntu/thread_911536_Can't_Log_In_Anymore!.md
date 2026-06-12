---
title: "Can't Log In Anymore!"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by CompBio on 2008-09-05
I was trying to get my Ubuntu laptop synchronized with a school machine using Unison.  In the process of switching back & forth between the machines, I executed the following command:

sudo chmod -R 750 .

Unfortunately, this was on my laptop rather than the remote machine.  I closed the window before I discovered that I could no longer open a window.

Now I can't log into my laptop!

How can I get it to accept my root login so I can change the permissions on those directories again?

Help??!

---

### Post by Peter09 on 2008-09-05
You will have to go in to safe mode.

Hit escape at the grub prompt and that will allow you to go into safe mode as root.

---

### Post by CompBio on 2008-09-05
Thanks!  It took a little hunting, but I found the correct login.

Crisis averted.  I owe you a beer. :tongue:

---

### Post by Crafty Kisses on 2008-09-05
> **CompBio said:**
> Thanks!  It took a little hunting, but I found the correct login.

Crisis averted.  I owe you a beer. :tongue:

Glad to hear, mark the thread solved. :)

---

### Post by Vadi on 2008-09-05
Check out [http://www.getdropbox.com](http://www.getdropbox.com), let me know if you want an invite... it's very easy to use, just install a .deb of their program, you get a folder you can drag and drop files into and it's automatically syncronized. No need to tinker with terminal commands :)

---

### Post by Peter09 on 2008-09-06
Glad to hear all is ok

---

