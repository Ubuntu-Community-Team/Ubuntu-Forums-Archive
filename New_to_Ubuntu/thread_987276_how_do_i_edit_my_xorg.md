---
title: "how do i edit my xorg?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by pcrussell50 on 2008-11-19
this is on a standard, 19" crt monitor...

...switched to ubu8.10, and now the resolutions i can select are 800x600, or 640x480.  i used to have many more choices.  when i select, system>preferences>screen resolution, there is a button that says "detect displays".  when i "press" that button, nothing happens at all. the default resolution was 800x600, even though i wanted 1024x768, it was still useable.  in my frustration, i selected 640x480, and now, when i go to system>preferences>screen resolution  and re-select 800x600, i can't see or get to the bottom button that says "apply" or something like that.  so now i'm stuck in 640x480 with a nearly unusable system.

i have an xorg.conf file that worked in a previous install of xubuntu saved, but i don't know the proper ubuntu editor that will allow me to replace the one i have.  for that matter i don't recall the proper xubuntu editor either.

-peter

---

### Post by pgatrick on 2008-11-19
If the gui stuff doesn't work then you probably will have to edit xorg.conf. It's pretty easy, just add the resolutions you need to it.
I usually use vim to edit it, but that's just what I'm used to and use for any cli editing. Also man xorg.conf should help. :)

EDIT: This is the section to add the resolutions to:
```
# Section "Screen"  
#     Identifier    "Default Screen"  
#     Device        "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"  
#     Monitor        "Generic Monitor"  
#     DefaultDepth    24  
#     SubSection "Display"  
#         Depth        24  
#        ** Modes        "1024x768"  **
#     EndSubSection  
# EndSection  
```

---

### Post by pytheas22 on 2008-11-19
If you want to open your xorg.conf file for editing in Ubuntu, type in a terminal:
```

sudo gedit /etc/X11/xorg.conf
```

In Xubuntu, you would type:
```

sudo mousepad /etc/X11/xorg.conf
```

You may also want to check the cable connecting the monitor to the computer.  If it's not securely connected at either end or is just going bad, that could be why the computer is unable to auto-detect higher resolutions.  I had this problem a while back and spent several hours fighting with xorg.conf before I finally thought to try a different VGA cable, which solved the problem instantly.

---

### Post by o.besner on 2008-11-19
Whatever your version of Buntu is, you can use nano. It comes pre-installed.

open a console and type "sudo nano /etc/X11/xorg.conf"

and voilà ! What you need to add is exactly what pgatrick said.

If you have an Nvidia card, you can also do "sudo nvidia-settings" and configure it with a friendly GUI.

---

