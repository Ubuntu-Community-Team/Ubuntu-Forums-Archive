---
title: "Dual monitors error"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by iPhQ on 2011-12-16
I have bought a new monitor and I have made ubuntu dual screen. When I restarted my computer I got this error message:
```
Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 354
CRTC 354: trying mode 3200x1080@50Hz with output at 1024x768@50Hz (pass 0)
CRTC 354: trying mode 3200x1080@50Hz with output at 1024x768@50Hz (pass 1)

```
How can I fix this?
Thanks!:confused:

---

### Post by oldos2er on 2011-12-16
Gave your thread a more meaningful title.

Which version of Ubuntu, which video card and drivers are you using? The more info you can provide, the better chance you have of getting good help.

---

### Post by iPhQ on 2011-12-16
> **oldos2er said:**
> Gave your thread a more meaningful title.

Which version of Ubuntu, which video card and drivers are you using? The more info you can provide, the better chance you have of getting good help.

Sorry for using an inappropriate title.
I am using ubuntu 11.10.
I'm not sure which video card drivers I am using but on my Additional Drivers thing it says NVIDIA accelerated graphics driver (version current) [Recommended].
My graphics card is: GeForce GT430.

---

### Post by pierreyy on 2011-12-16
hello.

have you tried disconnecting one monitor and restarting your pc?

---

### Post by iPhQ on 2011-12-16
> **pierreyy said:**
> hello.

have you tried disconnecting one monitor and restarting your pc?

Just did it. I got 4 errors now.
```

none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 354
CRTC 354: trying mode 3200x1080@50Hz with output at 1024x768@50Hz (pass 0)
CRTC 354: trying mode 3200x1080@51Hz with output at 1024x768@50Hz (pass 0)
CRTC 354: trying mode 3200x1080@50Hz with output at 1024x768@50Hz (pass 1)
CRTC 354: trying mode 3200x1080@51Hz with output at 1024x768@50Hz (pass 1)


```

EDIT:: Is it me or it says that my monitor is 3200x1080? If yes then that's wrong. I have set it to 1920x1080

---

### Post by DaveyG on 2011-12-16
[QUOTE=iPhQ]NVIDIA accelerated graphics driver (version current) [Recommended].[/QUOTE]

I find version 173 works better (for me; GeForce 6150 LE)... I had a few issues with the "recommended version"

---

### Post by iPhQ on 2011-12-16
> **DaveyG said:**
> I find version 173 works better (for me; GeForce 6150 LE)... I had a few issues with the "recommended version"

I have tried changing it too.
Didn't work.

---

### Post by oldos2er on 2011-12-16
Are you able to get to the desktop? If you can, try running ```
gksudo nvidia-settings
``` to set up your monitors, if you haven't already.

---

### Post by iPhQ on 2011-12-16
> **oldos2er said:**
> Are you able to get to the desktop? If you can, try running ```
gksudo nvidia-settings
``` to set up your monitors, if you haven't already.

Yes I am able to get to the desktop. I have used this to change my settings. It's just that when I turn my computer on ubuntu looks like windows 98 and I get the error message.

---

### Post by audiomick on 2011-12-16
> **iPhQ said:**
> Just did it. I got 4 errors now.
 Is it me or it says that my monitor is 3200x1080? If yes then that's wrong. I have set it to 1920x1080
This is likely to be a result of the attempt to get Twin View working, i.e. the nVidia way of spreading your desktop across two monitors. What it does is create a virtual screen as wide as both monitors put together (assuming they are side by side), and as high as the higher of the two (in pixels, not in physical size). If one of the two is not as high as the other, there will be a "dead space" above or below the smaller of the two, because the virtual screen is always rectangular.

---

### Post by iPhQ on 2011-12-16
> **audiomick said:**
> This is likely to be a result of the attempt to get Twin View working, i.e. the nVidia way of spreading your desktop across two monitors. What it does is create a virtual screen as wide as both monitors put together (assuming they are side by side), and as high as the higher of the two (in pixels, not in physical size). If one of the two is not as high as the other, there will be a "dead space" above or below the smaller of the two, because the virtual screen is always rectangular.

Could this be causing the error?

---

### Post by audiomick on 2011-12-16
I doubt it. What I described is normal behaviour. I had a setup running for several years through several updates with a 1280x1024 monitor and a 1024x768. It all worked fine. All I had to do after an update was start the nVidia config thing and tell it how I wanted it. In the more recent versions of Ubuntu, this was an entry in the system> administration menu. It can also be started using the command
```
gksu nvidia-settings
```.

As far as error messages goes, my 10.10 install shows me one when I boot up. It says something along the lines of
" the saved resolution is not supported".
It is not exactly that, because my computer is set to speak German. ;)
This came about after I disabled the nVidia driver to check on something for somebody, and then re-enabled it. I have no idea what is annoying it, and wont be looking as I intend to remove that install in the near future. Despite the error message, it boots fine, so I am just ignoring it.

---

### Post by iPhQ on 2011-12-17
So is there a away to fix it? It's kind of annoying. None of the icons are showing up. Except the theme changes when I click 'ok'.

---

### Post by themusicalduck on 2011-12-17
So you're saying that you can change the settings to how you'd like them to be, but the settings aren't persistent after a reboot? Not entirely sure if that's what you mean.

If that is the case, open up nvidia settings, set up your monitors and resolution to how you'd like, then click Save to X Configuration File and Save.

Hopefully after a reboot your monitors should be how you want them.

---

### Post by iPhQ on 2011-12-17
> **themusicalduck said:**
> So you're saying that you can change the settings to how you'd like them to be, but the settings aren't persistent after a reboot? Not entirely sure if that's what you mean.

If that is the case, open up nvidia settings, set up your monitors and resolution to how you'd like, then click Save to X Configuration File and Save.

Hopefully after a reboot your monitors should be how you want them.

I did that and it gave me the error. The monitor settings work correctly, but the icons do not show up properly.

---

