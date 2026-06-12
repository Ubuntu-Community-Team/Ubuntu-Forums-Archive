---
title: "landscape-client not configured"
date: 2012-08-02
forum: New to Ubuntu
---

### Post by AustenG on 2012-08-02
Hi, 

I recently was trying to get dual monitors to work with 12.04, but somehow messed something up (no surprise there).

Now, when I reboot it complains about 'landscape-client' not being configured, then says that I should run landscape-config - at this point it hangs and requires a hard shutdown. When I reboot into safe mode and go to root, the command 'landscape-config' (also 'sudo landscape-config') fails. It complains saying something like 'read only files.' Sorry I'm not more specific with the errors, I'm unable to copy anything and am now forced to use my Windows partition. 

Also, apt-get --fix-broken and other such apt-get commands do not work. 

Does anyone know what in the world is going on here? I seem to be at a standstill here - I'm hoping not to have to reinstall the os.

Thanks for any help!

---

### Post by AustenG on 2012-08-04
I've done a bit more research and realized this may all be an issue with lightdm. I've started x by doing ```
 startx 
```
which actually gives me my desktop back (albeit with terrible resolution - like 640x480; plus I don't have any tool bars or anything). 

Hope this clarifies a bit more..

---

### Post by madjr on 2012-08-04
seems you accidently activated landscape:

[http://freshtutorial.com/landscape-ubuntu-manage-ubuntu-infranstructure/](http://freshtutorial.com/landscape-ubuntu-manage-ubuntu-infranstructure/)


to change resolution, you may try this:

[http://www.youtube.com/watch?v=SQ_N-mQCmIc](http://www.youtube.com/watch?v=SQ_N-mQCmIc)

or

[http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html](http://www.vxbus.com/software/linux/148-how-to-change-monitor-resolution-in-ubuntu-1204.html)

[http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html](http://www.ubuntugeek.com/how-to-adjust-screen-resolution-on-ubuntu.html)

---

### Post by AustenG on 2012-08-04
For anyone reading this:

My issue with landscape client and not booting turned out to be another issue: the xorg.conf file. Accordingly, I am marking this as solved (even though I still haven't fixed the xorg.conf file issue).

---

