---
title: "Getting keyboard backlights to toggle on and off on XFCE?"
date: 2019-08-22
forum: New to Ubuntu
---

### Post by skeezyleff on 2019-08-22
I followed the instructions and wrote the various scripts from [this]("https://answers.launchpad.net/ubuntu/+source/linux/+question/241299") thread, such as the one in autostart, the LightDM config, and the original thing in a scripts folder I made in home.

It seems that they do not work, as when I booted up or came back from suspending, even when logging in they did not light up, only doing so with ```
xset led 3
``` 

I'm new to shell scripting, but it seems that there are mentions of GNOME and unity in the various scripts by user RickyB where I copied and pasted them from essentially, just switching some paths given my name. Granted, this may not be the only way to have my keyboard lights turn on and off using the screen lock key, but I'd prefer to do it this way as I'd like them on before I login, and I can turn it on and off with a key. It should be noted that the simplest way using the GUI in the "Session and Startup" section of the settings, putting in the simple command above does not work after I wake my computer after suspending it.

Any help would be greatly appreciated.

---

