---
title: "Unity top panel"
date: 2011-10-28
forum: New to Ubuntu
---

### Post by whiskeylover on 2011-10-28
Is there a way to hide it? I have to use Citrix for work, and it opens a window in full screen mode (or the same size as the entire desktop. This results in the Citrix window starting below the top panel, and a portion of it being hidden at the bottom.

I installed 11.10 today, and so far have been disappointed with the inability to tweak its setting :( It feels like I'm using a Mac.

---

### Post by whiskeylover on 2011-10-29
Anyone?

---

### Post by BillyBoa on 2011-10-29
Sorry but as far I know, there is only a compiz script to change position to Unity launcher
[http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html](http://www.webupd8.org/2011/10/how-to-move-unity-launcher-to-bottom-of.html)
For the upper panel, nothing.
In any case you can move to Gnome classic....

---

### Post by whiskeylover on 2011-10-29
Thanks Billy.

---

### Post by Frogs Hair on 2011-10-29
F11 still works for full screen .

---

### Post by nogoodnamesleft on 2011-10-29
> **whiskeylover said:**
> Is there a way to hide it? I have to use Citrix for work, and it opens a window in full screen mode (or the same size as the entire desktop. This results in the Citrix window starting below the top panel, and a portion of it being hidden at the bottom.

I installed 11.10 today, and so far have been disappointed with the inability to tweak its setting :( It feels like I'm using a Mac.

Actually the Mac UI is massively configurable but it uses secret hidden shortcuts that no-one can remeber.

If you're really having issue with 11.10 and unity desktop, I believe it's also available with xfce, or use maverick (Ubuntu 10.10, you can still download the installer from Ubuntu). Maverick is pretty stable and the gnome2 it uses is easily configurable.

---

### Post by beew on 2011-10-29
Yes, if it is the same as 11.04 you can install ccsm and go to Ubuntu Unity Plugin > Experimental and set panel opacity to 0

---

### Post by whiskeylover on 2011-11-06
Thanks for the suggestions guys. I chose to log on to Windows whenever I'm using Citrix, and log back into Ubuntu for everything else.

> **Frogs Hair said:**
> F11 still works for full screen .
Unfortunately Citrix doesn't work inside the browser. It is its own standalone application.

> **beew said:**
> Yes, if it is the same as 11.04 you can install  ccsm and go to Ubuntu Unity Plugin > Experimental and set panel  opacity to 0
That won't help either because the panel would still be there, even though totally transparent. And the Citrix window would start just below the panel. 

Thanks for the suggestions though.

---

### Post by 3rdalbum on 2011-11-06
Does it allow you to Alt-drag the window so you can see the bottom of the window?

---

### Post by Frogs Hair on 2011-11-06
> Unfortunately Citrix doesn't work inside the browser. It is its own standalone application.

F11 works for all applications unless I misunderstood  .

---

### Post by whiskeylover on 2011-11-15
> **3rdalbum said:**
> Does it allow you to Alt-drag the window so you can see the bottom of the window?

Yes, that works. But I'd rather have it covering the entire screen for a more productive experience.

> **Frogs Hair said:**
> F11 works for all applications unless I misunderstood  .

Hmm... I didn't know that. I'll have to try it when I go home in the evening.

---

### Post by 3rdalbum on 2011-11-15
> **Frogs Hair said:**
> F11 works for all applications unless I misunderstood  .

It's just a fairly well-observed shortcut, but certainly not all programs observe it. Libreoffice even has it mapped to perform some other function.

---

### Post by Frogs Hair on 2011-11-15
I don't use LO that much and certainly not at full screen , but you're correct that is the only exception I can find among the applications I most use .

---

### Post by Steeperton on 2011-11-15
I find that after opening ctirix, if  I minimise it, then maximise it, it redraws the screen to "fit" - that is you still have the Ubuntu top bar (so allowing me access to music & email notifications), but the "windows" citrix now fits fully in the remaining space (if that makes sense!), so I can access the windows bar.

---

### Post by whiskeylover on 2011-11-16
> **Steeperton said:**
> I find that after opening ctirix, if  I minimise it, then maximise it, it redraws the screen to "fit" - that is you still have the Ubuntu top bar (so allowing me access to music & email notifications), but the "windows" citrix now fits fully in the remaining space (if that makes sense!), so I can access the windows bar.

Doesn't work for me. The problem is Citrix window still "fits" in the remaining space, but the window is displaying a remote desktop session. And that session still uses the original size, and hence keeps getting trimmed at the bottom.

I've found a workaround for now. I move the window slightly up, so that the title bars of the windows inside the remote session get trimmed, but I can see the taskbar at the bottom.

---

### Post by Steeperton on 2011-11-16
Forgot to mention that I've set the screen size of citrix manually to 1600x900 (my monitor size) rather than seamless / no preferences (via the browser when I log in - I have to login via he browser, download an .ica file, then this launches citrix - not sure if it's the same for you).

Then the above min/maximise (when the remote desktop is fully loaded) works.

---

### Post by whiskeylover on 2011-11-16
> **Steeperton said:**
> Forgot to mention that I've set the screen size of citrix manually to 1600x900 (my monitor size) rather than seamless / no preferences (via the browser when I log in - I have to login via he browser, download an .ica file, then this launches citrix - not sure if it's the same for you).

Then the above min/maximise (when the remote desktop is fully loaded) works.

That's exactly how I use it. The only difference is, when clicking on the icon, it doesn't take me to the remote desktop preferences dialog box, instead it directly logs me in to my work computer. In short, it's not a shortcut to remote desktop, rather its a shortcut to the remote desktop bookmark set up by the admins.

So, I never see the settings screen. It directly takes me to the username/password dialog box of my work PC.

---

### Post by Steeperton on 2011-11-18
Not sure if yours is the same as mine, but I'll walk through it.
enter url for my work connection into firefox ([http://desktop.xxxxx.co.uk](http://desktop.xxxxx.co.uk))
enter username, password & safeword code
then I'm presented with list of icons (different desktops that I have permission to - under these, I have a couple of links, including "session preferences" - this is where I can change the screen resolution.

If that's not the case, then I'm out of ideas, I'm afraid!

---

### Post by whiskeylover on 2011-11-18
> **Steeperton said:**
> Not sure if yours is the same as mine, but I'll walk through it.
enter url for my work connection into firefox ([http://desktop.xxxxx.co.uk](http://desktop.xxxxx.co.uk))
enter username, password & safeword code
then I'm presented with list of icons (different desktops that I have permission to - under these, I have a couple of links, including "session preferences" - this is where I can change the screen resolution.

If that's not the case, then I'm out of ideas, I'm afraid!

I only have one icon after I login, for remoting into my home computer. It does not give me any preference screen, just takes me directly to the username/password screen. :)

Anyways, thanks for the help. Appreciate it.

---

### Post by redeemer on 2012-01-12
My solution was:

If you have Compiz enabled (as in Unity by default):

```

sudo apt-get install compizconfig-settings-manager

```

Then, in Control Center: Personal / CompizConfig Settings Manager
check Utility / Workarounds / Legacy Fullscreen Support.

---

