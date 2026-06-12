---
title: "cairo dock disappeared"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by seamustry on 2008-07-25
i installed cairo dock and it started up fine. but when i changed some settings like auto hide, position, etc. it just disappeared.

i did a complete removal in synaptic and then reinstalled it but now when i start the dock, it doesn't even show up. i can see the process running though. 

any suggestions as to how i can completely remove it, including its settings, etc?

---

### Post by Sealbhach on 2008-07-25
```
sudo aptitude purge cairo-dock
```

Should wipe out all trace of it I think.

.

---

### Post by northern lights on 2008-07-25
In your home folder, there's a hidden folder with the cairo-dock configuration. Remove before reinstallation (it might even render that unnecessary).

Either open your home folder, enable viewing hidden files (Ctrl+H) and delete ".cairo-dock" or run ```
rm -r /home/USER/.cairo-dock
```where USER needs to be replaced by your username.

---

### Post by seamustry on 2008-07-25
thanks for the help...i just deleted the files in .cairo-dock folder and restarted cairo dock which now is working

---

### Post by 4ebees on 2009-01-26
> **northern lights said:**
> In your home folder, there's a hidden folder with the cairo-dock configuration. Remove before reinstallation (it might even render that unnecessary).

Either open your home folder, enable viewing hidden files (Ctrl+H) and delete ".cairo-dock" or run ```
rm -r /home/USER/.cairo-dock
```where USER needs to be replaced by your username.

Thanks for that.

I've got 8.04.1 running on five machines (family :)) and this happened on one the kids machines. I found the:

.cairo-dock.conf

file here:

/home/<name>/.config/cairo-dock/current_theme

I removed that, log the user out and when I logged them back in, the dialog box for running Cairo-Dock came up...and now all is well :))

Many thanks.

---

### Post by northern lights on 2009-01-26
You're welcome.

In return, thank you for searching the forums rather than opening up a new, yet redundant, thread.

---

