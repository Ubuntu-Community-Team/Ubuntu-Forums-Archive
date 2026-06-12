---
title: "How can I remove Drop Box?"
date: 2014-01-07
forum: New to Ubuntu
---

### Post by gabmuks on 2014-01-07
Hello and good day to all.

I somehow installed a program called drop box while online.

I must have clicked on some advertisement.
Am not exactly sure how I did it.
Anyways, I tried to remove drop box with Ubuntu Software Center,
but it doesn't recognize that it is already installed on my computer.

Can anyone suggest a way to remove this "Drop Box"?

Thank you for your time.

---

### Post by boregard on 2014-01-07
hello, open terminal and type this command > sudo apt-get remove --purge dropbox nautilus-dropbox 

---

### Post by Frogs Hair on 2014-01-07
There is Dropbox  integration in the repository and the package is and the package is nautilus-dropbox. I don't know if that helps with removal of what you installed .

---

### Post by vasa1 on 2014-01-07
If you aren't using Dropbox just delete the **Dropbox** and **.dropbox** folders from your home folder and, in case you have it as an application set to run at start-up, click on the Xfce mouse, Settings, Sessions and Startup, Application Autostart and delete any Dropbox entry there.

---

### Post by mark65ak on 2014-01-08
FYI   I don't think you installed anything by clicking a web link.  Not in ubuntu.  Linux is protected from that kind of stuff.  That's a Bill Gates kinda thing with .exe .com and .dll files that execute.

---

### Post by gabmuks on 2014-01-08
> **boregard said:**
> hello, open terminal and type this command



Thanks much for your help!

Your answer is what I was hoping to find.
I don't know any code, but have been able to use it
by the cut and paste method.

Your answer did the trick. No more drop box.

I will mark thread as solved.

---

