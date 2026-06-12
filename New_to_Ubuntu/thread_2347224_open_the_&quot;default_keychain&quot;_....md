---
title: "open the &quot;default keychain&quot; ..."
date: 2016-12-22
forum: New to Ubuntu
---

### Post by abartomak on 2016-12-22
Everytime when I start my browser, I get this message; asking me to add the password of the default keychain (it's in finnish, I don't know how to translate it exactly)... I add the password and "open locking", so the pop-up goes away. I can also click CANCEL and it goes away.

Any idea how I can remove that pop-up totally?

---

### Post by Frogs Hair on 2016-12-22
Hello abartomak:

Is this the web browser and if so is a master password set in options > security ?

---

### Post by abartomak on 2016-12-23
yes, web browser (FlashPeak). I added LightLocker OFF now, will check if that works. In security of the browser there's "enable WebRTC" (it's ON), "disable reading from html5" (OFF), "always allow out-dated plugins to run" (ON)

---

### Post by abartomak on 2016-12-31
still the same problem exists...

I don't know where to find "master password set in options > security"

---

### Post by Frogs Hair on 2016-12-31
What Browser are you using ?

---

### Post by grahammechanical on 2016-12-31
Is the OS set to automatic login? This might help you.

[http://askubuntu.com/questions/495957/how-to-disable-the-unlock-your-keyring-popup](http://askubuntu.com/questions/495957/how-to-disable-the-unlock-your-keyring-popup)

I think that the correct English term is "keyring." 

Regards

---

### Post by yetimon_64 on 2017-01-03
> **abartomak said:**
> yes, web browser (FlashPeak)...

> **Frogs Hair said:**
> What Browser are you using ?

Could possibly be a cross-platform freeware licenced one from a "flashpeak" named website [[COLOR=#0000ff]--here--[/COLOR]]("http://www.flashpeak.com/")

The site offers two downloads of "slim browser" and "slimjet web browser"; both are for windows at that site. 
However I've also found [[COLOR=#0000ff]--this "slimjet" page--[/COLOR]]("http://www.slimjet.com/en/dlpage.php") with linux download links on it at a different site.

Cheers, yeti.

---

### Post by trivialpackets on 2017-01-03
I have most often found this if I had auto-login enabled.  Some have suggested setting it to a blank password, which does work to get rid of this alert but it is a bad practice security-wise.  Combined with the fact that you also may have auto-login enabled.  If you disable auto-login, this tends to disappear as the default key ring is opened when you authenticate at login and if you have auto-login enabled, my advice would be to disable it, rather than the protected key ring.

---

