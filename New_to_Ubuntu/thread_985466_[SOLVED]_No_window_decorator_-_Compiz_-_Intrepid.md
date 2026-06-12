---
title: "[SOLVED] No window decorator - Compiz - Intrepid"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by lduplantie on 2008-11-17
I finally succeeded installing Intrepid Ibex and the nvidia 96.43.09 driver for my card. The autodetection did not work and I had to manually edit the xorg.conf file and then used nvidia-setttings to select the proper screen resolution. There must be a better way but when you are newbie...

Now I that have the effects with compiz, I lost the window-decorator (no borders). Worse, when I start a terminal, I can't enter any commands. My only option is to disable the effects through System>Preference>Appearance.

I tired changing the command line in the compiz window decoration plugin to /usr/bin/gtk-window-decorator. No success.

Any idea for a solution?

Thanks

PS I have to edit my signature to show Ubuntu 8.10

---

### Post by jenkinbr on 2008-11-17
What card do you use?

---

### Post by lduplantie on 2008-11-17
Quadro2 MXR/EX/Go 32Mb

I know its probably marginal. but everything worked under 8.04 LTS

---

### Post by sirjoebob on 2008-11-17
I would install emerald-themes and use it as the window decorator.. That is what I use and it is great.

---

### Post by Crafty Kisses on 2008-11-17
Go into the Compiz Settings Manager and find "Windows Decorations" and make sure where it says "Decorations Window" it says the following:
```
any
```

---

### Post by lduplantie on 2008-11-17
How do I enable Emerald. I have installed it from Synaptic.

---

### Post by lduplantie on 2008-11-17
Thats what it is set at: any

---

### Post by Crafty Kisses on 2008-11-17
To enable Emerald you can press Alt+F2 and enter this at the prompt:
```
emerald --replace
```

---

### Post by jenkinbr on 2008-11-17
> **lduplantie said:**
> How do I enable Emerald. I have installed it from Synaptic.
I'm not sure what the official method of enabling emerald is - I've tried editign /usr/bin/compiz-decorator , but it gets overwritten everytime I update.

You could try opening gnome-session-proporties and add an entry titled 'emerald' with the command 'emerald --replace' to the list of startup programs.

---

### Post by sirjoebob on 2008-11-17
[QUOTE=jenkinbr;6200189
You could try opening gnome-session-proporties and add an entry titled 'emerald' with the command 'emerald --replace' to the list of startup programs.[/QUOTE]

This is what I have done. Works great 
:guitar:

---

### Post by lduplantie on 2008-11-17
I have modified the command line in the compiz decoration plugin to emerald --replace
No success
I have added a session command
emerald -- replace
No success
I have tried Alt+F2 emerald --replace
No success

---

### Post by Crafty Kisses on 2008-11-17
Do you have Window Decorations checked? I know that's a dumb question, but it's very possible.

---

### Post by sirjoebob on 2008-11-17
Try going to System>Preferences>Emerald.

Make sure you have a theme installed, if not, pick one up ([Gnome-look]("http://www.gnome-look.org")) and try it again. It may be running but just not have a theme to use.

---

### Post by lduplantie on 2008-11-17
Yes the window decoration plugin is selected
Yes I have selected a theme in Emerald

I have installed fusion icon and tried about every possible options there.
Only Metacity will activated window decoration

---

### Post by jenkinbr on 2008-11-17
fusion icon is an icon theme.  Try installing [this emerald package]("http://www.compiz-themes.org/content/download.php?content=93147&id=1&tan=36389607") into emerald theme manage and then issuing ```
emerald --replace
```

Note - [http://compiz-themes.org](http://compiz-themes.org) is better for emerald themes, although gnome-look.org has them as well...

---

### Post by lduplantie on 2008-11-17
I Installed the compiz.org theme.

Unfortunately it still does not work

---

### Post by lduplantie on 2008-11-17
Eureka!

I had another look at my xorg.conf file, and for some reason a line went missing (I guess by my mistake)

I added in the Screen section
Option   "AddARGBGLXVisuals"  "True"

and window decoration is now functional. 

Emerald is also working.

Thank you all for your help.

---

### Post by jenkinbr on 2008-11-17
Glad to hear!

---

### Post by lduplantie on 2008-11-17
Thanks

---

### Post by sirjoebob on 2008-11-17
Dont forget to mark thread as solved.

---

