---
title: "is there any way to suspend the laptop?"
date: 2018-06-06
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-06-06
just noticed i do not see any way to suspend my laptop?  any clues? thanks .

---

### Post by monkeybrain20122 on 2018-06-06
It suspends when I close the lid or choose suspend at the menu.

---

### Post by Impavidus on 2018-06-07
Have a look at the power settings. Where exactly you can find those depends on the flavour you're running. There you can select what to do when you close the lid, hit the power button, hit the suspend button etc.

---

### Post by leunam12 on 2018-06-07
Click on the top-right corner and then hold the ALT key, the ON/OFF symbol will turn into a PAUSE symbol. Click that and the laptop will suspend.
An alternative is to install pm-tools and then create a custom keyboard shortcut with the command "sudo pm-suspend".

---

### Post by bodhin2 on 2018-06-07
it is not in the menu.  that is why i asked.  i am  running plain ubuntu 18.04.

i did not see it in any power settings as such either.

i will try the alt key things - thanks.  and yes it appears.  many thanks.  i also found that in activitires - search 'suspend' and it also appears on screen.  the alt is better/

---

### Post by PaulW2U on 2018-06-07
The [Suspend Button]("https://extensions.gnome.org/extension/826/suspend-button/") extension eliminates the need to press ALT by adding a further button to the status menu.  :)

---

### Post by monkeybrain20122 on 2018-06-07
> **bodhin2 said:**
> it is not in the menu.  that is why i asked.  i am  running plain ubuntu 18.04.

i did not see it in any power settings as such either.

i will try the alt key things - thanks.  and yes it appears.  many thanks.  i also found that in activitires - search 'suspend' and it also appears on screen.  the alt is better/

I see.This is gnome shell, no wonder. :) Yeah you probably need an extension for that. You need an extension for every basic function in GS that they have removed or hidden because in their opinion you don't know how to use the computer if you don't do it their superior way.

---

### Post by bodhin2 on 2018-06-07
i have been wondering why they removed so much helpful stuff and added other apps they to me are useless.  as long as i can get a handle on this stuff....

---

### Post by PaulW2U on 2018-06-07
Seeing this thread while playing around with a new installation of Ubuntu prompted be to see if the extension was in the Ubuntu repositories or not. It is.

```
sudo apt install gnome-shell-extension-suspend-button
```

to install the extension. Then go into Tweaks | Extensions to turn it on.

I can't remember if you have to log out before the button shows. Hope that helps bodhin2.

---

### Post by bodhin2 on 2018-06-07
thanks - i may end up doing that.  i did see it before but not sure what works or exactly what some stuff actually does i did not want to add too much extraneous stuff.

---

### Post by bodhin2 on 2018-06-07
got it - thank you!!!!

---

