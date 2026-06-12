---
title: "Options disapeared"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by Dead root on 2011-09-12
Hello,

Few options in the top panel disapeared :
Click / Date / Keyboard / Log out

I don't see them anymore...How can i fix that?

---

### Post by ubudog on 2011-09-12
Hi, what version of Ubuntu are you using?

In 11.04, to reset Unity (including the clock, log out button, etc.), type this in a terminal:
```
unity --reset
```

In 10.10 and below (or Classic desktop in 11.04), you would do this:
```
gconftool &#8211; -recursive-unset /apps/panel && rm -rf ~/.gconf/apps/panel && pkill gnome-panel
```

Hope that helps!  ;)

---

### Post by Dead root on 2011-09-14
Thanks, I am using the classic desktop not unity.

When I typed the first command, my Laptop freezed and it stooped working so I had to restart it manually.

---

### Post by ubudog on 2011-09-14
> **Dead root said:**
> Thanks, I am using the classic desktop not unity.

When I typed the first command, my Laptop freezed and it stooped working so I had to restart it manually.

If you are using the Classic desktop, the first command won't work.

Try the second command while you're in the Classic desktop.  ;)

---

### Post by Dead root on 2011-09-14
The 2nd command didn't work either.

> gconftool – -recursive-unset /apps/panel && rm -rf ~/.gconf/apps/panel && pkill gnome-panel
Error while parsing options: Unknown option -recursive-unset.
Run 'gconftool --help' to see a full list of available command line options.


---

### Post by ubudog on 2011-09-14
Try:
```
gconftool --recursive-unset /apps/panel && rm -rf ~/.gconf/apps/panel && pkill gnome-panel
```

---

### Post by Dead root on 2011-09-15
Thanks it worked now :)

I am using Ubuntu 11.04 now it's possible to upgrade to the new version from it? once it's available? or I need to download the new version and Install it?

---

### Post by ubudog on 2011-09-15
> **Dead root said:**
> Thanks it worked now :)

I am using Ubuntu 11.04 now it's possible to upgrade to the new version from it? once it's available? or I need to download the new version and Install it?

Great!

Ubuntu 11.04 is the latest version.  When 11.10 is released, you can either upgrade using the Update Manager, or by doing a fresh install.  (backing your stuff, then copying it back in to the new install)

---

