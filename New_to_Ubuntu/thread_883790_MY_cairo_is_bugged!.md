---
title: "MY cairo is bugged!"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by MordL on 2008-08-08
ehhh i tried completed reinstallating didn't worked :<

(cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
cairo_dock_load_gauge (128x128 )
cairo_dock_load_gauge (128x128 )

this is the error i get atm any help plz? :D

it used to work till i setted it at the right pile then it bugged

---

### Post by pedro_orange on 2008-08-08
Make sure it's completely removed

```
dpkg -l | less
```

Then do a sudo apt-get install cairo-dock and post the output.

Also post the output of you attempting to run it from terminal if you can install it fine.

---

### Post by billgoldberg on 2008-08-08
> **pedro_orange said:**
> Make sure it's completely removed

```
dpkg -l | less
```

Then do a sudo apt-get install cairo-dock and post the output.

Also post the output of you attempting to run it from terminal if you can install it fine.

Cairo dock isn't in the repositories.

You'll need to reinstall it from the .deb files.

Completely remove cairo dock in synaptic and then look in you home folder (hidden files, press ctrl h) and delete the cairo-dock folder.

If there is any.

---

