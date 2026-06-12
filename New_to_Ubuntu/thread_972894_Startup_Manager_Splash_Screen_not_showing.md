---
title: "Startup Manager Splash Screen not showing"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by stevebond001 on 2008-11-06
Hi
I was running the startup manager with Hardy, and had an alternative Usplash screen loading at boot time.  Everythig was working fine until I upgraded to Intrepid.  Since then, my alternative splash screen does not show when booting up (just the boot text is seen).  Running startup manager does not show any errors, and I can use this to set the display the default Ubuntu splash screen when booting - I just can't get any other splash screens to work.
Has anyone else had the same problem?  If so, is there a fix?

Thanks in advance.

---

### Post by philinux on 2008-11-06
You can try this fix.
[https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/235615](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/235615)

---

### Post by stevebond001 on 2008-11-06
Thanks philinux.
I tried running the Startup Manager with sudo, changed the splash screen and exited, but this made no difference when rebooting (I still see boot text and no graphic)

---

### Post by philinux on 2008-11-06
Have you tried the command line method of install usplash?

---

### Post by stevebond001 on 2008-11-06
I have followed the commands in the link from your previous post (substituting my own .so file.  everything was configured OK and no error messages were seen.  However, when I reboot I still get no splash screen, just the boot text.
It seems peculiar though because when I use the Startup Manager to set the boot screen to the default Ubuntu screen, it works perfectly.

---

### Post by philinux on 2008-11-06
[http://ubuntuforums.org/showthread.php?t=746132](http://ubuntuforums.org/showthread.php?t=746132)

I'd start with post 16

---

### Post by stevebond001 on 2008-11-06
Looks like this thread deals with suspend issues as well (which I don't seem to have).
I followed the thread (and tried the suggestions listed) but still to no avail.  I just don't get a splash screen other than the default Ubuntu one, when using Stertup Manager.

Perhaps I'll have to put up with this until a newer version is released.

---

### Post by kestal on 2008-11-06
Is this a problem for you on Intrepid? I run both Hardy and Intrepid and the only culprit seems to be 8.10 (I am running 32-bit). You're not alone.

---

### Post by stevebond001 on 2008-11-06
Yes this is only a problem for me since I upgraded to Intrepid.  When I was running Hardy it worked perfectly (both on 32-bit)

Glad I'm not alone in this ](*,) - So hopefully some clever person will point us both in the right direction

---

### Post by philinux on 2008-11-06
> **stevebond001 said:**
> Looks like this thread deals with suspend issues as well (which I don't seem to have).
I followed the thread (and tried the suggestions listed) but still to no avail.  I just don't get a splash screen other than the default Ubuntu one, when using Stertup Manager.

Perhaps I'll have to put up with this until a newer version is released.

I'd raise a bug at launchpad then.

---

### Post by stevebond001 on 2008-11-06
How do I do that then?  Sorry to be a pain, but I've never done that before.

---

### Post by philinux on 2008-11-06
Go here. [https://bugs.launchpad.net/](https://bugs.launchpad.net/) Click report bug. I think it will then ask you to register. Then you can report a bug. Posting a bug is similar to raising a thread on here. One thing to watch is the box that says package. Make sure you put startup-manager in it. This ensures the package devs see the bug.

I've also found this.
gnome-splashscreen-manager it's in synaptic. It might work where SUM failed if there's a bug in SUM.
[edit] ^ dont bother with this it crashes.

---

### Post by stevebond001 on 2008-11-06
philinux
thanks very much for the help - I'll raise a bug in a little while.

Thanks once again

---

### Post by stevebond001 on 2008-11-07
philinux
Rather than raise a new bug for this, I have added to bug number 235615 (which I believe that you created).  Details are as follows:
[https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/235615](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/235615) 

If I get a resolution I will post back here to let everyone know.

---

