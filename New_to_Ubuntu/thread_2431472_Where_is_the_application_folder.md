---
title: "Where is the application folder?"
date: 2019-11-16
forum: New to Ubuntu
---

### Post by abigairey2806 on 2019-11-16
there should be a route like this: 
~/.local/share/applications 

But i cant find the applications i just can get to the share folder, what im trying to do actually is to put putty as my default telnet/ssh handler so ill be able to enter to putty from my browser

---

### Post by CatKiller on 2019-11-17
The ~ represents your home folder.

Directories that start with a . are hidden by default. You can use Ctrl-H in most file browsers to show hidden files.

---

### Post by abigairey2806 on 2019-11-17
Thanks, but in the share folder there is:  
gvfs-metada 
keyrings
 libgda 
recently-used.xbel 
trash

but application no where to be found,  i used ls -a to see the hidden files and is no there

---

### Post by CatKiller on 2019-11-17
That just means that you haven't played around with editing menus or installing stuff locally. That directory isn't like "Program Files," if that's what you're thinking. It just contains launchers specific to your user to use as menu entries or on the panel. It's the per-user equivalent of /usr/share/applications. The .desktop files in there are just text files. You can create the directory if there's something that you want to put there. 

You may have a particular use case, but PuTTY is primarily a Windows application to allow it to have tools like the ones you get with Linux. You already have the means to connect via SSH out of the box. I'd also be very uncomfortable with a browser being able to start an SSH session without user intervention.

---

### Post by abigairey2806 on 2019-11-17
Thanks Cat, that is helpful

---

