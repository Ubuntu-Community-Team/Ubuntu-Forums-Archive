---
title: "Graphics/Monitor setup, and anything else that may be useful"
date: 2012-12-16
forum: New to Ubuntu
---

### Post by ChaosBringer255 on 2012-12-16
Hello ubuntu forums,

I'm not new to linux but ive not used ubuntu studio before and had a few questions that i couldnt figure out via google and such.

Anyway, I just installed ubuntu studio and the main thing that is really irritating me is the lack of extended display support in the display settings feature. I have a Acer Aspire 5750g laptop with a nvidia gt540m graphics card, running an external monitor through the HDMI port.

Anyway, how I would like it to be set up is the external monitor be running as my main monitor, with the applications menu and bar on it, and the laptop monitor as a secondary, extended monitor to either side of the main.

using xrandr i was able to set the monitors apart, however its not permanent and resets after logoff. And even so, it does not set the external as the main monitor. I tried other methods from multiple different websites, as well as attempted installing manually the nvidia graphics drivers, but that gave me an error, and every method i have read so far tells me to modify files which were not included in this system install?

ex- xorg.conf (main one that pops up, not in my system )

I'm running Ubuntu Studio 12.10, fresh install. I will refrain from changing any settings until I can get some help.

And another thing, how well would my audio interface (NI Komplete Audio 6) work with ardour/ubuntu without being able to install the komplete audio 6 control panel?

---

### Post by DuckHook on 2012-12-16
It's a common irritation in some installations with NVidia cards. Settings have to be changed as root, but NVidia settings control panel doesn't challenge for password and switch to root when it should.

Do either <Alt>+<F2>, or <Ctrl>+<Alt>+<t> for terminal, then:

```
gksudo nvidia-settings
```Make the appropriate changes to your settings. Logout/login. They should now be permanent.

If you have a xorg.conf file, settings there will override your changes. 12.10 doesn't need a xorg.conf, so unless you have a really odd configuration, get rid of it, and your new settings will now work.

---

### Post by ChaosBringer255 on 2012-12-17
> **DuckHook said:**
> It's a common irritation in some installations with NVidia cards. Settings have to be changed as root, but NVidia settings control panel doesn't challenge for password and switch to root when it should.

Do either <Alt>+<F2>, or <Ctrl>+<Alt>+<t> for terminal, then:

```
gksudo nvidia-settings
```Make the appropriate changes to your settings. Logout/login. They should now be permanent.

If you have a xorg.conf file, settings there will override your changes. 12.10 doesn't need a xorg.conf, so unless you have a really odd configuration, get rid of it, and your new settings will now work.

I failed to mention that I dont have the official nvidia drivers installed, and that my laptop has the "optimus" style card ie its probably running with my onboard graphics card for the main settings.

I am able to change the position using xrandr, but they dont save. and using nvidia-settings just spits out some sort of error (ill reboot momentarily and find out what it was)

edit: scratch that it returns no error, it just doesnt do anything. i tried installing the nvidia drivers but i couldnt seem to get that to work

either way theres gotta be a way to just set the generic display settings to split the monitors permanently? (xrandr --output works but its not permanent and it doesnt change primary monitor)

---

### Post by ubu_dynamite on 2013-01-11
I don,t have experience with optimus but you could try to get the nvidia card working with bumblebee probably you can use nvidia-settings then.

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://bumblebee-project.org/](http://bumblebee-project.org/)

---

