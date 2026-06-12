---
title: "screwed up screen resolution"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Brutus2006 on 2008-04-25
I installed 8.04 install went fine, But of course screen resolution is out, I install envyng and set up install Nvidia drivers. Screen was way out of wack, couldnt adjust anything. I unistalled and reinstalled thought maybe that was my problem now I get on my monitor "Analog out of range" 106.0khz/85hz and nothing else balck screen.
I have Nvidia 5500 card. 

Not sure what to do next.

Why cant the Ubuntu team figure this out its always a constant problem. Maybe for the next update

Anyhelp would be appreciated

---

### Post by alienexplorers on 2008-04-26
First off if you are using the nvidia-glx-new driver deselect it in Envy.  Unload all drivers using Envy.  Select manual mode and select the middle driver (96.43.05).  This loads nvidia-glx.  Restart gdm by doing a ctrl-alt-backspace.  Now run nvidia-setting like this:
> sudo nvidia-settings
select the resolution and refresh rate you want.

---

