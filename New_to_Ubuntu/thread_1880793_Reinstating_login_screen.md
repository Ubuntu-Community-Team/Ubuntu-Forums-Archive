---
title: "Reinstating login screen"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by daithi23 on 2011-11-14
Hi, I recently installed lubuntu 11.10 and decided not to go for login screen by default but now I can't find a way to turn it on.
I chose lubuntu for speed but after trying to change the wallpaper and the look of it I now don't know if I'm running LXDE, Gnome, Openbox or a combination of these. I wasn't even sure what they were until yesterday (and I'm still a bit foggy on it!). I want to get the login screen back and change the default login to LXDE please! Maybe after that I can play around with the rest of it but at the moment let's go with the basics!
A big thank you!

---

### Post by jjex22 on 2011-11-14
try Ctrl+Alt+Backspace

Edit Just noticed ... welcome to  the forums!

---

### Post by daithi23 on 2011-11-14
Ctrl+Alt+Backspace does nothing. What's it supposed to do?
I should have mentioned after playing around with backgrounds, the Openbox Configuration Manaager, some themes and icons the last few days I now just turn the computer on then logout and log back in choosing LXDE...
P.S. Thanks for the welcome! Having a few teething problems but feels liberating to be away from Windows!

---

### Post by daithi23 on 2011-11-17
Hmmm, seeing as it was a new install I just started over and installed again. This time not messing with the settings til I know what I'm doing...

---

### Post by Rodney9 on 2011-11-17
Welcome and I'm sure you'll enjoy [COLOR="Blue"]Lubuntu[/COLOR] as much as I do.

You would be best to log in to [COLOR="Blue"]'Lubuntu'[/COLOR] rather than 'LXDE', [COLOR="Blue"]Lubuntu[/COLOR] will look much nicer,

For How-To's, Information and Screen-Casts on [COLOR="Blue"]Lubuntu[/COLOR] go to the -

[Lubuntu One Stop Thread]("http://ubuntuforums.org/showthread.php?t=1844755") 

Rodney

---

### Post by marinara on 2011-11-17
there's a tutorial for enabling auto-login here:
[http://www.omgubuntu.co.uk/2011/11/five-handy-lubuntu-tips/](http://www.omgubuntu.co.uk/2011/11/five-handy-lubuntu-tips/)

To disable auto-login... I'll just put a '#' on that line.

Let me test it.

**edit**
It works fine here.  For some reason gksudo is broken on my box already.  But regular sudo works fine.

TL;DR:

[LIST]
[*]sudo leafpad /etc/lxdm/default.conf
[*]put a '#' on the autologin=myusername line
[/LIST]

---

