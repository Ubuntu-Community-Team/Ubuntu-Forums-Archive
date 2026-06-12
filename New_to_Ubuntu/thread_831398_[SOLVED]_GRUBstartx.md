---
title: "[SOLVED] GRUB/startx"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by AnLGP on 2008-06-16
Hello,

Currently when I log in GRUB must wait for 5 seconds to boot the selected OS.  I only have one OS on this computer and am aware waiting has its benefits, for sure.  I would like to bypass this and was wondering if all I had to do was edit this:

> ## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

to "0" where the 5 is (no quotes).

Also,

After GRUB gets done it goes thru some stuff (just words on the screen) and I still have to login (which I don't mind) and then type "startx" before it will load directly to enlightenment (someone helped me with that earlier).

Is there a way I can just log in and *not* have to type startx in after that?  I don't want a login manager or anything like that.  If it can't be done just let me know.  Please and thanks :)

---

### Post by drs305 on 2008-06-16
You can edit it but there is also Startup-Manager (System, Admin, Startup-Manager). You can edit a variety of behaviors of the grub menu from this app.

If you don't have it:
```
sudo aptitude install startupmanager
```

For more on your grub editing options:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

But to answer your question, Yes, you can put it at 0 - however I would recommend at least 1 second so you can intervene should you ever want to boot into recovery or a different kernel.

---

### Post by AnLGP on 2008-06-16
ok thanks I'll move it to 1.

Any idea about the "startx" thing, anyone?

---

### Post by drs305 on 2008-06-16
> **AnLGP said:**
> Any idea about the "startx" thing, anyone?

So when you boot your machine it ends up at a console and you have to type "startx" at that point to get to the Desktop? If this is the case I'd mark this thread as solved since a lot of people will think this is a GRUB issue and start a new one with a title like "Must Type startx to boot to gui" or something similar. I think you would get more responses.

Best of luck. I'm sure someone will have an answer for you.

---

### Post by blacappuccino on 2008-06-16
Hey guys i installed Ubuntu on a PC with windows but i want to remove the GRUB to boot windows without starts from GRUB. The first time i formated the Ubuntu partition but it destroyed the GRUB and i couldn't boot windows. I had to install again the Ubuntu including GRUB.

     So tell me how i can active the windows partition cos i don't want to depend on GRUB.

     Thanks

---

