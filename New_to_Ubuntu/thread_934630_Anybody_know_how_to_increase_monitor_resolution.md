---
title: "Anybody know how to increase monitor resolution?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by ctothebizza on 2008-09-30
OK, so for most people this probably isn't that big of a deal, but I guess I'm being picky.  I have an HP 1702 monitor.  For some reason, I can't get the resolution to go up to 1280 x 1024 which is supposed to be the native resolution.  It will only go up to 1024 x 768 so everything looks kind of fuzzy and big.  When I click on system, preferences, and then screen resolution, it doesn't even give me the option of a higher resolution.  It says unknown on the picture of the monitor, so I don't think it knows what monitor I have.  I have an Nvidia 8800 GT graphics card, too, if that is a help...  Thanks!

---

### Post by robalcorn on 2008-09-30
Do you have the restricted driver running? If so go to Applications/Accessories/Terminal and type : sudo nvidia-settings. From there you can select resolutions of choice and it will save your settings.

---

### Post by shazbut on 2008-09-30
I sometimes have to force the correct monitor type by running displayconfig-gtk from the terminal to enable the higher resolutions.

---

### Post by ctothebizza on 2008-09-30
Ok, I do have the restricted driver running, but when I type in sudo nvidia-settings, it says "sudo: nvidia-settings: command not found"  Do I have to install nvidia settings?

---

### Post by robalcorn on 2008-09-30
> **ctothebizza said:**
> Ok, I do have the restricted driver running, but when I type in sudo nvidia-settings, it says "sudo: nvidia-settings: command not found"  Do I have to install nvidia settings?

sorry in terminal type : sudo apt-get install nvidia-settings
than you should be good to go

---

### Post by cariboo on 2008-09-30
If you are running Hardy open up a terminal and run:

```
sudo displayconfig-gtk
```

This will setup the modlines in your /etc/X11/xorg.conf. You should now be able to set the resolution that your monitor is capable.

Jim

---

### Post by ctothebizza on 2008-09-30
ok, so I ran sudo displayconfig-gtk, and it said that my monitor was just plug-and-play, so I went and changed that to the correct monitor.  I then chose the correct resolution and restarted.  When the computer booted up, the login screen was giant (only half of the word ubuntu was on the screen and the user box was in the bottom right corner of the screen.  I ran sudo displayconfig-gtk again, and it still says the correct monitor, but the proper resolution isn't there, and the refresh rate is at like 52.??  I then tried to run the nvidia-settings, and it says that I have a "lite-on h15aau" monitor, and it won't let me change that, or increase the resolution....Is it possible that my monitor is broken and won't go up to the higher resolutions?  Does that happen?

---

### Post by robalcorn on 2008-09-30
> **ctothebizza said:**
> ok, so I ran sudo displayconfig-gtk, and it said that my monitor was just plug-and-play, so I went and changed that to the correct monitor.  I then chose the correct resolution and restarted.  When the computer booted up, the login screen was giant (only half of the word ubuntu was on the screen and the user box was in the bottom right corner of the screen.  I ran sudo displayconfig-gtk again, and it still says the correct monitor, but the proper resolution isn't there, and the refresh rate is at like 52.??  I then tried to run the nvidia-settings, and it says that I have a "lite-on h15aau" monitor, and it won't let me change that, or increase the resolution....Is it possible that my monitor is broken and won't go up to the higher resolutions?  Does that happen?


Thats weird, I would try undoing this and run sudo displayconfig-gtk again and set back to the way you found it originally and try sudo nvidia-settings again. Trial n error as it goes but one or the other should have resolved your problem?

---

### Post by ctothebizza on 2008-09-30
Ok, this is really wacky.  Now I tried sudo displayconfig-gtk again, and just selected a generic flat screen monitor and told it to go to 1280 x 1024.  Well, I think that it is now outputting at 1280 x 1024, but the monitor didn't adjust for it.  What I mean is that the whole screen won't fit on the monitor at one time, but if I move my mouse pointer to the edge, it smoothly scolls over so I can see it.  It like the computer is in the right resolution, but my monitor can't show it, but I know my monitor is capable of 1280 x 1024.  any ideas??

---

### Post by robalcorn on 2008-09-30
> **ctothebizza said:**
> Ok, this is really wacky.  Now I tried sudo displayconfig-gtk again, and just selected a generic flat screen monitor and told it to go to 1280 x 1024.  Well, I think that it is now outputting at 1280 x 1024, but the monitor didn't adjust for it.  What I mean is that the whole screen won't fit on the monitor at one time, but if I move my mouse pointer to the edge, it smoothly scolls over so I can see it.  It like the computer is in the right resolution, but my monitor can't show it, but I know my monitor is capable of 1280 x 1024.  any ideas??


Try setting it back to the original 1024x768 you first posted and yes your monitor can handle 1280 x 1024

---

### Post by ctothebizza on 2008-09-30
Ok, I'm pretty much back where I started.  I ran displayconfig-gtk and set it back to plug-n-play, but the only resolution it let me use was 640 x 480, which made everything extremely large.  So I put it back on the hp 1702, and restarted.  When I checked, it had changed it to the lite-on monitor again.  So now I am pretty much back where I started, and if I run the nvidia-settings, it still shows that i have a lite-on monitor, and doesn't allow me to change to the correct resolution.  Is there some way I can test my monitor to make sure it is working properly?

---

### Post by robalcorn on 2008-09-30
> **ctothebizza said:**
> Ok, I'm pretty much back where I started.  I ran displayconfig-gtk and set it back to plug-n-play, but the only resolution it let me use was 640 x 480, which made everything extremely large.  So I put it back on the hp 1702, and restarted.  When I checked, it had changed it to the lite-on monitor again.  So now I am pretty much back where I started, and if I run the nvidia-settings, it still shows that i have a lite-on monitor, and doesn't allow me to change to the correct resolution.  Is there some way I can test my monitor to make sure it is working properly?


with displayconfig-gtk these are the refresh rates of different resolutions to try that is for your monitor:

1280 x 1024 @ 60 Hz and 75 Hz
1024 x 768 @ 60 Hz, 70 Hz, and 75 Hz
800 x 600 @ 60 Hz, 72 Hz, and 75 Hz
640 x 480 @ 60 Hz, 72 Hz, and 75 Hz

why you get the wrong monitor vendor is strange. As for using the nvidia settings not letting you change is really strange..you are running it sudo nvidia-settings? There is an option for Detect Displays..did you try that? As for a test for you monitor none that i am aware of but maybe someone else might know.

---

### Post by ctothebizza on 2008-09-30
Yes, I am running as sudo.  I did try to click on detect displays and nothing happens.  In nvidia-settings, it won't let me change my monitor to anything else.  Something else that is weird:  I borrowed my brothers monitor, and it worked at the higher resolutions.  Then, when I plugged mine back in, it worked too, until I logged off, and it won't go back unless I plug his in first.

---

### Post by robalcorn on 2008-09-30
That is really weird does sound like there might be a problem with yours assuming your brothers is the same model. You could set back to normal res with your brothers to get yours going again and also look to see if there is an auto or reset button on the monitor.

---

