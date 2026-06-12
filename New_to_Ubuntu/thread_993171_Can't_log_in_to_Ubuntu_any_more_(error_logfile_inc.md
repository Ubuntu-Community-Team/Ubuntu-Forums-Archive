---
title: "Can't log in to Ubuntu any more (error logfile included)"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by susanne260 on 2008-11-25
I was just browsing the web with Firefox, and adding some new DNS servers in the nm-applet GUI, when all of a sudden X crashed. When I tried to log back in, it said: "Your session only lasted less than 10 seconds" and suggested me to try the Failsafe Gnome sesssion option, but that also gave the exact same "less than 10 seconds" error. Here's the error logfile:

~/.xsession-errors says:
```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

(seahorse-agent:6050): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(seahorse-agent:6050): atk-bridge-WARNING **: IOR not set.

(seahorse-agent:6050): atk-bridge-WARNING **: Could not locate registry
Xlib:  extension "XEVIE" missing on display ":0.0".
SESSION_MANAGER=local/ubuntudream:/tmp/.ICE-unix/6050

```

Also, if I hit CTRL+ALT+F1, log in, and type "sudo shutdown -r now" it says "Segmentation fault". What does that mean? :-k

I'm using Ubuntu 8.04.1 Hardy Heron.


(posting this thread from windows xp)

---

### Post by saru411 on 2008-11-25
Have you tried hitting ESC while GRUB is loading and then booting to RECOVERY MODE, then pick XFIX. This will attempt to fix X. I doubt it will work but it can't hurt.

---

### Post by chata on 2008-11-25
> **saru411 said:**
> Have you tried hitting ESC while GRUB is loading and then booting to RECOVERY MODE, then pick XFIX. This will attempt to fix X. I doubt it will work but it can't hurt.


Yea, tried that.  Didn't work.  :(

---

### Post by susanne260 on 2008-11-25
> **saru411 said:**
> Have you tried hitting ESC while GRUB is loading and then booting to RECOVERY MODE, then pick XFIX. This will attempt to fix X. I doubt it will work but it can't hurt.

Yup, that didn't do anything, unfortunately. :\

> **chata said:**
> Yea, tried that.  Didn't work.  :(

Heh, do you also have the **exact** same problem? :D
Otherwise you might want to create a new thread.

---

### Post by susanne260 on 2008-11-26
I'm kind of wondering **what caused this problem**. In that session I didn't change any of the settings that might have affected X in any way, so I'm really clueless here...

Perhaps there are some logfiles or something I could post that may help investigate this problem? =)

---

### Post by susanne260 on 2008-11-27
I googled for "*Xlib extension XEVIE missing on display :0.0."* and found out that I could try adding these lines to xorg.conf:

```

Section "Extensions"
        Option "XEVIE" "Enable"
EndSection

```

So, using nano I added those lines to xorg.conf. I didn't get the same error message as before, but this time it said: *"Assistive technology support has been requested for this session, but the accessibility registry was not found. Please ensure that the AT-SPI package is installed. Your session has been started without assistive technology support."*

Assistive technology support? Where did that come from? :D
I don't remember having any of that enabled...

Anyway, I hit CTRL+ALT+F1 and entered "sudo apt-get install at-spi" and it said "Segmentation Fault". Then I entered "sudo shutdown -r now", and that also gave the "Segmentation Fault" error. 

Finally I decided to try CTRL+ALT+DEL, which actually did restart the computer. So, then I went to root shell in the the "recovery mode". After entering "sudo apt-get install at-spi", it said that the at-spi package is already installed.

Now I really don't know what to try any more. :neutral:

---

### Post by susanne260 on 2008-11-28
Ok... I don't know what else to do, so I guess I'm going to reinstall Ubuntu...

---

