---
title: "I want to change the login background on xubuntu 11.10 beta1"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by peterbe on 2011-09-12
I have installed Xubuntu 11.10 beta1, with updates up to today. The background to the login screen is an ugly solid purple color. I would like to know how to change that to an image.

On other Ubuntu versions, such as Ubuntu 11.04 'natty', I generally use "Ubuntu Tweak" to do this, but this is not available yet for Oneiric, and I don't know if it works for any Xubuntu versions anyway.

There may be a built-in menu option for this in earlier Xubuntu releases, but it's not in the menus for Oneiric, so far.

Is there some file I can change to do this, if a utility doesn't exist yet?

---

### Post by Krytarik on 2011-09-12
Since Xubuntu 11.10, too, uses LightDM as the display manager, try this:

[http://www.webupd8.org/2011/09/how-to-change-lightdm-login-screen.html](http://www.webupd8.org/2011/09/how-to-change-lightdm-login-screen.html)

And please give feedback about what scaling method it applies, since there is apparently no option to set.

Greetings.

---

### Post by Toz on 2011-09-12
In _Xubuntu_ 11.10, the file to edit is **/etc/lightdm/lightdm-gtk-greeter.conf**. The value to change is as per the link referenced above - **background=**

---

### Post by peterbe on 2011-09-12
Thank you, Toz and Krytarik!

That works fine, I was able to change the background.

---

### Post by overdrank on 2011-09-13
Moved to Ubuntu +1 (Oneiric Ocelot) :)

---

