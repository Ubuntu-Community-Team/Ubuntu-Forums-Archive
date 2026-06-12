---
title: "Installing drivers, video driver in particular. . . direct x?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by cinohpa on 2008-06-26
So, completely new to ubuntu. I've done a lot of running around in the synaptic package manager and I dl'd the nvidia driver, but my machine never asked me to restart and I'm still having problems with things I thought installing the video driver would fix. 

I've been trying to run some old games in wine that the wine website says work (warcraft III in particular) and have been getting crazy errors. I think it might have something to do with my video driver or maybe direct x. Do I need a substitute for direct x? 

Any other driver related things I need to find for my machine to make things run properly? I don't know anything about what I need to find for my machine versus what ubuntu can compensate for.

Thanks.

---

### Post by eapache on 2008-06-26
What is your graphics card? Is it fast enough to run WoW?

Go to System->Administration->Hardware Drivers and make sure that everything says 'in use'. If it isn't, enable it then restart.

Ubuntu does OpenGL instead of DirectX, but wine is supposed to provide compatibility.

Sorry I can't be of more help.

---

### Post by cinohpa on 2008-06-26
yes my grahpics card is fast enough for wow. (8600m GT) I'm running a laptop though which could complicate things.

I checked out the file path that you mentioned I didn't see anything about the drivers though. The closest tab I found under system>administration was hardware testing. It seems I failed the tests that I probably needed to prove my video/audio drivers were working, but only sent a report about it and didn't really seem to offer me any options. 

I thought I enabled drivers through the synaptic package manager, not that that's really seemed to work so far either though.

Thanks for the advice.

---

### Post by RomeReactor on 2008-06-26
Hi. Which version of Ubuntu do you have? If it's Hardy (8.04), and you can't see the Hardware Drivers entry in the Administration menu, open a terminal and paste:
```
gksudo jockey-gtk
```
This will bring up the application eapache mentioned.

While you're at the terminal, run this to see if your card has hardware acceleration enabled:
```
glxinfo | grep rendering
```
It should return 'Yes'.

What errors are you getting trying to run the game?

---

### Post by cinohpa on 2008-06-26
Yea it's hardy. It seems hardware acceleration isn't on as this is what the glxinfo command returned:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0". 
```

Thanks for the other tip. Do I need to restart before I can see the mentioned menu option? I still don't see it after doing the first command and putting in the password and etc.

As far as the game errors go, I'll probably just keep researching it if it's still a problem after figuring out this driver stuff. I'd need to try to reinstall the games to get the errors again.

---

### Post by RomeReactor on 2008-06-26
> **cinohpa said:**
> Do I need to restart before I can see the mentioned menu option? I still don't see it after doing the first command and putting in the password and etc.
That application should be installed by default on your system. Try this other application: look in 'Applications->Other->Screens and Graphics'. If you don't see it, you can edit the menus (right-click on the menu in the top panel and select "Edit menus"). Or, to open it from the terminal:
```
gksudo displayconfig-gtk
```

Once it opens, go to the second tab (Graphics card) and look for the nVidia driver. 

Also please post the output of this:
```
cat /etc/X11/xorg.conf | grep Driver
```

---

### Post by cinohpa on 2008-06-26
Oh man. So I went in to the screens and graphics menu and found that no driver was installed/running so I enabled the nvidia option. Now my display is 640 X 480 when it was some much better much higher res, wide screen resolution. I guess I should change this back before I jump off a bridge or give up on ubuntu. 

Fortunately even with severe screen cramping I was able to find my way back to the terminal to look at what you asked about. 

```
 cinohpa@Cinohpa:~$ cat /etc/X11/xorg.conf | grep Driver
	Driver		"kbd"
	Driver		"mouse"
	Driver		"synaptics"
	Driver		"nv"
	Driver		"nv"

``` 

Thanks again.Logging off for the night so I won't be able to try anything until tomorrow night.

---

### Post by RomeReactor on 2008-06-26
> Driver		"nv"

The **nv** is the open source driver; it doesn't have hardware acceleration. Choose the **nvidia** driver in Screens and Graphics.

---

### Post by Xiong Chiamiov on 2008-06-27
And in case you need it, here's a [howto for NVIDIA + Hardy]("http://ubuntuforums.org/showthread.php?p=4978329#post4978329").

---

