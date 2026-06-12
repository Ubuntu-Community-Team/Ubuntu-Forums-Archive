---
title: "After opening firefox via &quot;sudo firefox&quot;, my non-root firefox broke"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by inktri on 2008-08-20
While logged into my non-root account, I opened firefox with "sudo firefox" to check for updates. After closing the root firefox and reopening the non-root firefox, I was distraught to find all of my bookmarks missing and the back/forward/reload buttons non-functional (eg. back button remains "grayed out" despite visiting pages consecutively). Strangely though, under the root firefox (sudo firefox), my bookmarks now appear. 

Anybody know what's going on and how I can remedy the situation?

Thanks for the help

---

### Post by aloshbennett on 2008-08-20
My guess is, firefox changed the permissions of some of your mozilla profile folders to root.

If you find any file under your profile directory owned by root, try changing the ownership back to you.

---

### Post by jordanmthomas on 2008-08-20
```
sudo chown -R $USER:users ~/.mozilla
```
See if this fixes it back.

---

### Post by Paqman on 2008-08-20
This, incidentally is why you should always use gksu/gksudo or kdesu to launch graphical apps.

There's no need to launch Firefox as root to check for updates, btw. The normal update system will alert you if a newer version is available in the repos.

---

### Post by Too Late on 2008-08-20
You could also try to start firefox in terminal like this:
```
firefox -profilemanager
```
Especially, creating a new profile when sudoing might prevent that problem. (Although I have never had those problems while starting firefox with sudo.)

---

### Post by Bliepo32 on 2008-08-20
Why would you want to run firefox with root anyway? So it can scr*w up your files if you get malware from a site?

---

