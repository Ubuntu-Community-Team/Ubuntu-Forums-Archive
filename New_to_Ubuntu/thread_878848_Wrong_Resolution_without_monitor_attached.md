---
title: "Wrong Resolution without monitor attached"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by kool_kat_os on 2008-08-03
When ubuntu boots up with out a monitor attached it boots up at  800x600 instead of 1280x1024 when a monitor is attached

how do i make it so that if there is not a monitor attached...it boots up at 1280x1024 without a monitor attached?



Thanks

---

### Post by coffeecat on 2008-08-03
> **kool_kat_os said:**
> how do i make it so that if there is not a monitor attached...it boots up at 1280x1024 without a monitor attached?

Short answer - you can't. This is a failsafe mechanism in the xserver. If it can't detect a monitor it defaults back to 800x600.

Why are you booting up without a monitor?

---

### Post by kool_kat_os on 2008-08-03
> **coffeecat said:**
> Short answer - you can't. This is a failsafe mechanism in the xserver. If it can't detect a monitor it defaults back to 800x600.

Why are you booting up without a monitor?

im using it as a server

---

### Post by coffeecat on 2008-08-03
> **kool_kat_os said:**
> im using it as a server

Yes, I can see that would be a problem. I'm sorry I couldn't offer anything more constructive. If there is a hack to fix this, it's probably an obscure one. Because the beginner's forum is very busy, it might be worth bumping this thread occasionally to see if anyone knows of one. Alternatively you could use the report button on your own post to ask the admins to move the thread to a quieter subforum, perhaps General Help or even Server Platforms.

---

### Post by blue_shift on 2008-08-03
Silly question maybe, but why should it matter what the resolution is if there is no screen in use? Are you using a remote screen or something?

---

### Post by CatKiller on 2008-08-03
If, when X starts up it can't detect a monitor, it defaults to a low-resolution. This is the cause of most of the "my resolution is too low" posts.

You can tell X what frequencies to use, and to ignore anything else. You do this by editing xorg.conf: ```
sudo nano /etc/X11/xorg.conf
```

To tell it to ignore everything else, put ```
        Option          "UseEDID"                       "False"
``` at the end of the **Device** section. To tell it which frequencies to use, you need to get the numbers from the documentation for your monitor. These go in the **Monitor** section. For example, my Monitor section looks like this: ```
Section "Monitor"
        Identifier      "Eizo F77"
        Option          "DPMS"
        HorizSync       30-95
        VertRefresh     50-160
        DisplaySize     402 300
EndSection
``` Just replace my numbers with your own and X should always start up in 1280x1024 regardless of whether there's a monitor connected. And regardless of what the monitor can do, so don't start it up with a monitor that can't handle that resolution or you might break it.

EDIT: of course, there might be an option in whatever software you're using to connect to specify a different resolution without fiddling with X.

---

### Post by kool_kat_os on 2008-08-03
> **blue_shift said:**
> Silly question maybe, but why should it matter what the resolution is if there is no screen in use? Are you using a remote screen or something?

its a browsershots.org server

---

### Post by cariboo on 2008-08-03
Instead of using a gui to administer your server, why not install a web based management suite like wembin. you can try out webmin here:

[http://www.webmin.com/](http://www.webmin.com/)

on the left hand side click on Demo and Screenshots and try it out.

For help installing webmin go here:

[http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html](http://onlyubuntu.blogspot.com/2007/05/how-to-install-webmin-in-ubuntu.html)

Jim

---

