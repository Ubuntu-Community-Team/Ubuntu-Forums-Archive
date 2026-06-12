---
title: "gaming mouse software"
date: 2016-03-06
forum: New to Ubuntu
---

### Post by luca47 on 2016-03-06
hello guys, so i'm wanting to switch to ubuntu, but i am wondering if i will be able to install my mouse drivers
the website does not support it, and i wouldn't want to lose the ability to choose my dpi settings, profiles, macros and other of sorts.
i use the natec genesis gx44, here is a link to the mouse: [http://genesis-zone.com/en/product/gx44-optical-gaming-mouse/](http://genesis-zone.com/en/product/gx44-optical-gaming-mouse/)

---

### Post by mastablasta on 2016-03-07
it says:
> System requirements

[LIST]
[*]Windows XP, Vista, 7, 8
[*]Windows 10(PLUG&PLAY)
[*]Mac OS X 10.5 i nowsze (PLUG&PLAY)
[*]Chrome OS (PLUG&PLAY)
[*][COLOR=#FF0000]**Linux kernel 2.6+ (PLUG&PLAY)**[/COLOR]
[/LIST]


so I guess you are good to go. you may need to adjust settings manually. often drivers are provided in kernel, but various setup software and guis for driver are not. there is usually some config files where one can change parameters if there is no GUI.

---

### Post by luca47 on 2016-03-07
it does work, but i do not know how i am to change all my mouse settings, since i don't have the mouse driver. i have heard it rumoured that i might be able to do it through wine. is that true?

---

### Post by mastablasta on 2016-03-07
well this would be a question for the manufacturer. since they claim to support Linux...

I don't know how they handle it in Linux. wine might be able to install software and you might even use it to generate some sort of config file with it. but how to go from there is anyone's guess as the file will probably be set for windows.

you could try to do it the hard core way for example: [http://askubuntu.com/questions/205676/how-to-change-mouse-speed-sensitivity](http://askubuntu.com/questions/205676/how-to-change-mouse-speed-sensitivity)
or: [https://patrickmn.com/aside/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/](https://patrickmn.com/aside/lowering-gaming-mouse-sensitivity-in-ubuntu-9-10/)
or: [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)
or: [http://www.gdargaud.net/Hack/LinuxMouse.html](http://www.gdargaud.net/Hack/LinuxMouse.html)
more on multiple buttons: [http://askubuntu.com/questions/152297/how-to-configure-extra-buttons-in-logitech-mouse](http://askubuntu.com/questions/152297/how-to-configure-extra-buttons-in-logitech-mouse)

the problem is that all these methods seem kind of messy. though they might work. in Linux you can do a lot of things. it just that there often isn't a GUI for it.

in this case - why the mouse doesn't have the configuration GUI is again the question for the one that made the mouse.

---

### Post by luca47 on 2016-03-10
thank you very much my friend!

---

### Post by Bucky Ball on 2016-03-10
Wine is an awful lot of kludge to get a mouse going. If you're not going to use Wine for anything else, I'd try and avoid it.

---

### Post by Crimple on 2016-03-11
When it comes to gaming mice one option is to install the respective software on a Windows machine/partition/VM, chose the settings and let the mouse store them. This way when you connect the mouse to whichever machine your choices will be there.
The limitation is that not all brands have in device storage, I know that Logitech and Roccat do.

---

