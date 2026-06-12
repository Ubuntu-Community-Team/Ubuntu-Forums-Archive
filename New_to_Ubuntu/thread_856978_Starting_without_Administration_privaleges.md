---
title: "Starting without Administration privaleges"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by watto_one on 2008-07-12
Please help with away to fix the following problem after I log in.

[COLOR="Red"]Starting without administration privileges[/COLOR].
You will not be able to apply any changes but you can still export the marked changes or create a download script for them.

After closing the warning Synaptic starts automatically.

Thanks in advance.

---

### Post by iaculallad on 2008-07-12
Try doing this:

Login as root using the terminal:

```
sudo su
```

then:

```
usermod -a -G admin your_user_name_here
```

---

### Post by ChameleonDave on 2008-07-12
It seems to me that Synaptic is autostarting because your desktop environment (Xfce) is saving your session.

You need to either get it to start with the clean session, or to exclude Synaptic from the programs that can be saved.

The reason why Synaptic ought not to be autostarted is that it needs to be started with admin privileges, which cannot be done automatically.

---

### Post by watto_one on 2008-07-12
I have looked at Synaptic and can't find how to change the auto start.

---

### Post by watto_one on 2008-07-12
iaculallad Thank you for your quick reply I will try your suggestion on next log in.

---

### Post by jimmy the saint on 2008-07-12
I had this same problem.  Go to Applications>Settings>Settings Manager and open the "Sessions and Startup" dialog.  Uncheck the "Auotomatically save session on logout" checkbox and restart the system.  For some reason simply logging out didn't make it take effect for me, so I had to do a full restart.

---

### Post by watto_one on 2008-07-12
Thanks Jimmy, Already checked that it wasn't ticked. 

Icaulallad tried what you said but must admit once I had done that I couldn't work out how to get the session to start. if at all possible could I have some more info please.

---

### Post by jimmy the saint on 2008-07-12
I just remembered what I had to do to finalize it.  Make sure that the "prompt on logout" box it checked.  When you go to shutdown or logout make sure that the "save session for future logins" is NOT checked.  For some reason the system pays attention to that, but not the main setting.  This should fix it!!

---

### Post by ChameleonDave on 2008-07-12
> **iaculallad said:**
> Try doing this:

Login as root using the terminal:

```
sudo su
```then:

```
usermod -a -G admin your_user_name_here
```
I think that you're trying to give him admin privileges there.  That's not what we need to do.

---

### Post by watto_one on 2008-07-13
Thanks Jimmy Am already setup as you suggest. Guess I'll just have to put up with the warning message for now.

---

### Post by aysiu on 2008-07-13
Well, it's really a three-part process.

1. [Make sure you have *admin* privileges on your account.](http://www.psychocats.net/ubuntu/fixsudo)

2. Make sure if you are launching Synaptic, you launch it with the command ```
gksudo synaptic
``` or ```
gksu synaptic
```

3. Remove Synaptic from autostart or don't save your session.

---

### Post by watto_one on 2008-07-15
Sudo does work for normal stuff. The message just appears when i log in at start, Synaptic opens automatically when I close the warning message. 

I will do all you said on the weekend to see what happens.

---

### Post by watto_one on 2008-07-19
I have followed your advise with no change. My user name came up as already in admin. If I open Synaptic from the menu all works ok. The message at startup is still there though.

---

