---
title: "ViewSonic Monitor driver help?"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by jonathan_bravo2 on 2013-10-21
So today was the first time turning on my laptop in little over a week!?!? Yeah I know <---- anyways my question to you all is after I did all these updates for Ubuntu 13.10 I plugged up my corded keyboard, my wireless mouse, and my ViewSonic monitor up to my laptop Lenovo T61. Now at first I thought it was resetting itself due to the update, well about after the 3rd time in a row I figured okay something is going on. Anyway after I shut off my computer I unplugged anything and turned it back on. So I connected the mouse first it was fine everything was working okay, connected the keyboard same thing working fine also. Finally I connect the monitor and wouldn't you know it my computer freezes and reboots again. So I came to the conclusion that it's my monitor that's making it do all this and I was just wondering if anyone had the same problem and how do you fix it? I've already been to the ViewSonic website and looked up my monitor but it only has drivers and such for windows and mac..... NO LINUX??? Help please.

---

### Post by Dennis N on 2013-10-21
What model Viewsonic monitor are we talking about?

---

### Post by jonathan_bravo2 on 2013-10-21
> **Dennis N said:**
> What model Viewsonic monitor are we talking about?


It's a ViewSonic VX2753MH-LED

---

### Post by jonathan_bravo2 on 2013-10-24
So can anyone shed any light on this? Now I have another issue not sure if it has to do with the monitor but now every time I turn my computer on I have this message that says "Could not apply the stored configuration for monitors"

Error: on line 1 char 1: Document must begin with an element

---

### Post by CatKiller on 2013-10-26
I believe the monitor configuration is stored in ~/.config/monitors.xml. You could either look at the file to see if there's an obvious problem with it or just rename it to something else. A new one will be generated the next time you set your resolution.

---

### Post by jonathan_bravo2 on 2013-10-27
It's not my resolution that is the problem. It's the screen itself. Once I plug up my monitor to my laptop it appears to work just fine but after a minute or two the screen goes black and then my laptop resets itself. And keeps doing so until I unplug the monitor.

---

### Post by CatKiller on 2013-10-27
"Could not apply the stored configuration for monitors." That's where the configuration for monitors is stored.

---

### Post by jonathan_bravo2 on 2013-10-27
It says permission denied? Do you think this has anything to do with my graphics card or maybe my BIOS? I tried connecting to 2 other monitors that I own and the same thing happens...

---

### Post by CatKiller on 2013-10-28
It shouldn't do; you should be able to fiddle with almost everything in your Home directory. Perhaps that's the source of your problem?

---

### Post by jonathan_bravo2 on 2013-10-28
are you certain that is the way its supposed to be typed?         ~/.config/monitors.xml
I asked my friend to look into it for me since he has more time than I do but he said that the command did not do anything for him? Just making sure it's right before I do something else as my last resort which i hope it doesn't have to come down to.

---

### Post by CatKiller on 2013-10-28
It's not a command, it's a path.

~ means your Home directory.

.config is a directory inside it (files starting with a . are hidden by default, but Ctrl-h will show them).

monitors.xml is an XML file inside that.

I'm on 13.04, and it's possible that it's somewhere else in 13.10, but I doubt it. It's been there for at least five years.

---

### Post by jonathan_bravo2 on 2013-11-17
Man this post has been no help and there doesn't seem to be anything very helpful here or searching in Google. Whats crazy is that my monitor works when I make it the primary monitor but as soon as i try to make it my secondary screen there goes my laptop rebooting itself again. Oh well I suppose i'll just have to use my screen the way it is.

---

