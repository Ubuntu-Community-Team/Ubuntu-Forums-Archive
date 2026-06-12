---
title: "System won't boot after Natty upgrade (and gnome 3 downgrade)"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by readitsideways on 2012-04-16
Hi

I ran the updates to upgrade to Natty. Then I upgraded to Gnome 3, tried it and didn't like it (Desktop icons on Unity disappeared). I then removed gnome 3 (following these instructions for the upgrade and removal: 

[http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html](http://www.ubuntugeek.com/how-to-install-gnome3-on-ubuntu-11-04-nattyubuntu-10-10-maverick.html)
)

Now when I boot it hangs on *Checking battery state ..."

Inserting an Ubuntu boot CD doesn't boot to the CD (CD is first in the boot order) but this has been an issue for a while shich is why I did the upgrade rather than a fresh install.

Is there a way to get to the command line and fix this?

---

### Post by bogan on 2012-04-16
> Is there a way to get to the command line and fix this?Pressing 'Ctrl+Alt+F1' or F2 should give you a tty -Text Terminal - login prompt; enter your username and then Password - nothing will show - and press 'Enter'.

Edit: > Now when I boot it hangs on [or after] *Checking battery state ..." This usually means a problem with the Video driver or Xserver.

Chao!, bogan.

---

### Post by PhantomTurtle on 2012-04-16
Try this instead - [http://www.ajopaul.com/2011/04/26/ubuntu-11-04-uninstall-gnome3-and-revert-to-gnome-2-x/]("http://www.ajopaul.com/2011/04/26/ubuntu-11-04-uninstall-gnome3-and-revert-to-gnome-2-x/")(you may have to scroll down a bit). If you want GNOME 3, don't do it in 11.04, it already comes with Ubuntu 11.10.

---

### Post by dzponce11 on 2012-04-19
It would help to say why you downgraded.

---

