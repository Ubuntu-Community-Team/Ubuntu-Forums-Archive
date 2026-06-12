---
title: "What command to use?"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by spottiedogman on 2008-06-14
Hi Everyone,

I am new to unbuntu and linux and want to find out if everything is working right. Is there a command for system info like ram,processor speed,video memory, etc..? Think I have a video card issue but don't know for sure.

spottiedogman

---

### Post by SunnyRabbiera on 2008-06-14
well for basic system info there is the gnome system monitor, located in system> administration> system monitor

---

### Post by sdennie on 2008-06-14
I would try this:

```

sudo lshw -html > hardware.html

```

That will create a file called hardware.html which you can then open in a web browser (double clicking on it should do the job).

---

### Post by spottiedogman on 2008-06-14
Thanks SunnyRabbiera,

That helps with everything I needed except video ram, that was to easy see what a newbie I am!:rolleyes:

---

### Post by spottiedogman on 2008-06-14
Hi vor,

Thanks!that command string is awesome, I now know things I had no idea about. One thing that I'm trying to arrive at is my onboard video memory, I recall that this card had 32mb and I just don't see it. The reason I ask is that when I try and turn on visual effects it says they can't be enabled, I would think that my 32mb ATI Radeon Mobility M6 LY could at least muster normal visual effects but won't. What do you think I should do next?:confused:

spottiedogman

---

### Post by sdennie on 2008-06-14
What is the output of:

```

glxinfo | grep direct

```

If it says, "No", then you may not have the correct driver installed.  You may want to search these forums or google to see how to setup your exact card.

---

### Post by spottiedogman on 2008-06-14
vor,

direct rendering: Yes

Tried to use some instructions for the exact card, messes everything up, had to reload unbuntu.

spottiedogman

---

### Post by sdennie on 2008-06-14
The output of the following command might be useful:

```

compiz --replace &

```

It will probably fail but, the error message might tell you why.  If it does fail and you lose window borders and such, type the following to get back to normal:

```

metacity --replace &
disown

```

---

### Post by spottiedogman on 2008-06-14
this is what I got

donnie@donnie-linuxpc:~$ compiz --replace &
Checking for Xgl: [1] 7916
donnie@donnie-linuxpc:~$ not present. 
FATAL: Module battery not found.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4c59 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1366x1200) to maximum 3D texture size (512): Failed.
aborting and using fallback: /usr/bin/metacity

---

### Post by sdennie on 2008-06-15
Unfortunately, that sounds like you don't have enough video RAM to run compiz at the resolution you want to run it at.  There may be workarounds to force it to run anyway but, I don't have any experience with that.

---

