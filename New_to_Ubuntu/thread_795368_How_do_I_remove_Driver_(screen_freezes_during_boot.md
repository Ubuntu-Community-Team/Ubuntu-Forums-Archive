---
title: "How do I remove Driver? (screen freezes during bootup)"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by metasolaris on 2008-05-15
Hi,

I made the mistake of installing the 'restricted driver' Hardy offered me. This causes the screen to freeze during bootup so I cant get into the OS to remove it, Any ideas on how to remove it without having to reinstall Hardy (again)!

Thanks

meta

---

### Post by timandjulz on 2008-05-15
Guessing here: When you boot, choose recovery mode.  You should get the option to run terminal mode instead of GUI.

Once you have logged in you should be able to reconfigure x windows.  There is probably a handy way to do this that someone else knows.  I have manually edited /etc/X11/xorg.conf

Once reconfigured you can start X again via: startx

Another option, remove the driver via aptitude.  For example, if the driver is for ATI then:

sudo apt-get remove xorg-driver-fglrx

Or run "sudo aptitude" to get access to all installed packages.  Use "/" to enter search mode and type "restricted".  + will add packages, - removes them.  "G" go'es and changes the packages you marked.

Good luck,
Tim

---

### Post by amingv on 2008-05-15
> **timandjulz said:**
> Once reconfigured you can start X again via: startx

Don't startx from  the single-user root shell! Better restart your computer in normal mode with

```
shutdown -r now
```

---

