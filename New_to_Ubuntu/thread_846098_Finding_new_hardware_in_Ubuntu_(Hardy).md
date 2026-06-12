---
title: "Finding new hardware in Ubuntu (Hardy)"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2008-07-01
**[SIZE="4"]What is the tool in Ubuntu to detect hardware?[/SIZE]**

There must be one, but where is it?  Hardware testing is not what I mean. 
I have 2 monitors hooked up (1 DVI one VGA) but xrandr is only showing "Screen 0". (Yesterday I had VGA 0 and DVI 0).  I cannot complete my dual monitor setup without knowing these names.

Please help with this, it may be very simple, but it will save me hours more work to know just HOW to make Ubuntu see both monitors.

Thanks in advance!

---

### Post by Tatty on 2008-07-01
Try the screens and graphics manager.  It used to be in the system menu but seems to have disappeared in hardy, but you can get it via:

```
gksu displayconfig-gtk
```

Before you do that though make sure you backup your xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.my.backup
```

***EDIT:***

OR

If you are using the proprietry nvidia drivers you can use nvidia's own configuration tool:

```
gksu nvidia-settings
```

---

### Post by Motorhead Kaze on 2008-07-01
.

---

### Post by Motorhead Kaze on 2008-07-01
Thanks so much for your reply. I found the Screens and Graphics in System/Prefs/Main Menu/applications/other/screens and graphics (thanks to someone in another post).  Heck of an Easter Egg hunt that one!

My issue actually turned out to be that I had turned ON the propriety drivers for my graphics card, and SOMEHOW that was "Hiding" my second monitor from Hardy. Once I turned that off, I was able to make my edit to xorg.conf and arrange my dual monitors in the Screen Resolution pref window.

I feel so relieved now... 10 hours on this mothaa.  Thanks again for doing your part.

Peace.

---

### Post by Tatty on 2008-07-01
Oh excellent, I was not aware that it was sitting unactivated in the menus.  Thanks for that one.

Glad you got it working, shame you could not use the proprietry drivers with it though.  There must be a way to do that somehow, buried away on google somewhere... :)

---

### Post by Motorhead Kaze on 2008-07-01
Well, the guy/gal who wrote the advice about the propriety drivers said to turn them on again once the monitor was set up. Weird.  But hey, I don't require understanding every time...though I like it, not required.

---

