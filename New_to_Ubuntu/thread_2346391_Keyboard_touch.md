---
title: "Keyboard touch"
date: 2016-12-14
forum: New to Ubuntu
---

### Post by sakthiganesh on 2016-12-14
Hi Recently Dual booted Ubuntu with Windows 10 on my msi gs70 6qe stealth pro. I have a peculiar issue I can type my login password and login, I can use keyboard. But Whenever I open my terminal I cant type anything in the terminal and I cant type anything in firefox if I open firefox ....
And touchpad not working

Installed ubuntu developers edition 16.0 LTS

---

### Post by DuckHook on 2016-12-15
Welcome to the forums, sakthiganesh

Yours is the second issue with mouse and keyboard that I've run across on these forums in two days. I begin to suspect a problem in a kernel upgrade. If you can, try downloading a 14.04 LiveUSB and running it. If everything runs properly, post back results of:```
lsusb
``````
sudo lshw -sanitize
``````
xinput --list
```Output will be large so please post it between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Also, does keyboard work with other apps? Does keyboard work in CLI TTY? <Ctrl>+<Alt>+<F1>

EDIT

Also, try an external keyboard & mouse to see if you can at least effectively work on your machine.

---

