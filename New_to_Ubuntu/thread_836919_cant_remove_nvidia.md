---
title: "cant remove nvidia?"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Valk01 on 2008-06-22
Curious. trying to get my 7900gt to work under hardy. it does work, but only with minimal functionality. 

so i did a search on installing the nvidia, then did the apt-get nvidia-glx. whcih didnt seem to work for some reason. then i read about the envy installer for it. 

trying to do that, it comes up with this error that happens if i try to install envy, or just delete nvidia-glx. 

```
E: nvidia-glx: subprocess post-removal script returned error exit status 2

```

---

### Post by Mikecore on 2008-06-22
just open your "add remove" program manager and do a search for "nvidia"
make sure your setup to see "all available applications" at the top it will list the latest nvidia driver and just install it from there.

---

### Post by Valk01 on 2008-06-22
ok. got it all setup, but now, whenever i want to enable all the fancy stuff, everything like titlebars and the terminal is all whited out. any reason for that?

had to get nvidia working by reinstalling it before i could get envy to work.

---

### Post by alienexplorers on 2008-06-22
Paste this line into your xorg.conf file:
> Option         "AddARGBGLXVisuals" "True"

---

### Post by cariboo on 2008-06-22
There is a bug in the nvidia-glx-new removal script. I can't remember and I didn't document the bug number, but there is a work around for the problem. Check [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Jim

---

### Post by Valk01 on 2008-06-22
alright. got it to work by going through synaptic and reinstalling the nvidia-glx. then i was able to install envy.

getting multiple monitors to work, that was a fun challenge lol. but the twinview is working as i want now. 

anyone have any idea why vlc is gayly ignoring my second monitor in fullscreen? whenever it goes to fullscreen, it will just do it on the primary no matter what. video plays on the second display, but not in fullscreen =(

---

### Post by waspbr on 2008-06-22
Sorry to intrude but I have a related problem. I have a GF N6200 and the glx-new drivers break one of my favourite games, unreal 2004, So every now and then I revert to the nvidia-glx, but they break compiz... every compiz related stuff gets whited out...

so I added the line above

> Option "AddARGBGLXVisuals" "True" 

I added to xorg.conf as follows

```

Section "ServerFlags"
...
    Option "AddARGBGLXVisuals" "True" 
EndSection
```

However compiz is still broken,  I am only able to use terminal after doing

```
metacity --replace
```

any pointers?

---

