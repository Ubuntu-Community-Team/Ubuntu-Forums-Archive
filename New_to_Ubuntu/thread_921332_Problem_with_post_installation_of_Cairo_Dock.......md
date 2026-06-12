---
title: "Problem with post installation of Cairo Dock........."
date: 2008-09-16
forum: New to Ubuntu
---

### Post by jakewc2 on 2008-09-16
HI, sorry if this is the wrong place to post this but I just installed Cairo dock, using this thread 

[http://sudan.ubuntuforums.com/showthread.php?t=613087](http://sudan.ubuntuforums.com/showthread.php?t=613087)

using METHOD 1, using the 64bit Debian packages

I have it working, up to a pont, but I'm getting a few error messages , when I open a terminal and enter cairo-dock

here are the error messages, 

> jakewc2@jakewc2-desktop:~$ cairo-dock
warning :  (cairo-dock-modules.c:cairo_dock_preload_module_from_directory:254)  
  Attention : Attention : while opening module '/usr/lib/cairo-dock/libcd-xfce-integration.so' : (libthunar-vfs-1.so.2: cannot open shared object file: No such file or directory)
cairo_dock_create_surface_from_image: assertion `cImagePath != NULL && cairo_status (pSourceContext) == CAIRO_STATUS_SUCCESS' failed
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/jakewc2/.cairo-dock/current_theme/launchers/trash_empty.png': No such file or directory
warning :  (cairo-dock-surface-factory.c:cairo_dock_create_surface_from_image:352)  
  Attention : Failed to open file '/home/jakewc2/.cairo-dock/current_theme/launchers/trash_full.png': No such file or directory
warning :  (applet-init.c:_load_theme:72)  
  Attention : couldn't find images, this theme is not valid

the dock appears at the bottom of the screan, and I can configure it as well.

plus, when it first opened, it bought up a window that showed updates, but it then dissappeared.

Does anybody have any ideas what the error message means, and how I can sort it out? 

Thank you,

John.

edit: it appears that there is a lot of warnings appearing when I'm trying to configure it, so I have a feeling its not installed properly. :( Even though following the instructions seem to be quite easy. :(

---

### Post by whitethorn on 2008-09-16
Hi, I have pretty much the same problem but cairo dock still works.  What I figured out is you need to have 2 instances of it open. So start the program twice.  

At the moment I have it set up to show when I press a button.  That way I don't have a doc on my screen but if I need to open a program I press tilda and it appears.. Anyway I'm hoping someone has an idea how to fix this.

---

### Post by jakewc2 on 2008-09-16
I havent done that yet. What is tilda? I think I'm missing something?

---

### Post by fabounet on 2008-09-16
> '/home/jakewc2/.cairo-dock/current_theme/launchers/trash_empty.png': No such file or directory
there are some image's path in the theme you selected, which is not nice (all the themes should only define local path)
look into the config of the Dustbin applet, and erase these 2 adresses.
the warning about the module '/usr/lib/cairo-dock/libcd-xfce-integration.so' is normal because you don't have the XFCE libs on your PC, I don't know how to remove this warning but you can safely ignore it.

---

### Post by jakewc2 on 2008-09-16
Hi fabounet, I looked in the directory, and couldnt find the files, I think thats why I am getting the errors because they arent there.

---

### Post by fabounet on 2008-09-17
of course they are not, they are pointing to the user directory of the guy who made the theme ^_^
that's a bug, distant themes need to be cleaned a little.
you should just erase these 2 paths in the Dustbin config.

---

