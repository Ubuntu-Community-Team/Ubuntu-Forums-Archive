---
title: "Lubuntu 11.10; &quot;Don't ask for password at login&quot; is grey and uncheckable"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by diablo75 on 2012-04-18
I'm playing around with Lubuntu right now to get ready for putting it on a very old system and I'd like to be able to set it up so that it doesn't ask the user for their account password and automatically log them in, like you can do in Ubuntu.  This is a fresh install in a VM and I can't seem to figure out how to enable this option.  Any ideas?

---

### Post by JC Cheloven on 2012-04-18
Hi, at /etc/lxdm/default.conf, after [base], put a line that reads:
```
autologin=yourusernamehere
```
(put your username as convenient) and reboot. That should be it.

EDIT: here you can find a lot of very useful info about LUbuntu (thaks to forumite amijjawad):
[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)

---

### Post by diablo75 on 2012-04-18
Hey thanks a lot!  That did the trick.  Also the link you provided is very helpful; thanks!

---

### Post by JC Cheloven on 2012-04-21
> **diablo75 said:**
> Hey thanks a lot!  That did the trick.  Also the link you provided is very helpful; thanks!
You're very welcome!  :guitar:

BTW, at the time to install to your old computer, you'll be asked whether a user should be automatically logged in. If you choose that at this time, you don't have to tweak anything afterwards.

---

### Post by diablo75 on 2012-04-21
> **JC Cheloven said:**
> You're very welcome!  :guitar:

BTW, at the time to install to your old computer, you'll be asked whether a user should be automatically logged in. If you choose that at this time, you don't have to tweak anything afterwards.

I would have done that were it actually an option.  Try lubuntu in a vm sometime and you'll see ;)

---

### Post by JC Cheloven on 2012-04-21
> **diablo75 said:**
> I would have done that were it actually an option.  Try lubuntu in a vm sometime and you'll see ;)
Hi, I did that, mainly out of curiosity (a VB install should behave just the same as a 'real' one). I listened some music from your signature meanwhile. Ah, that modern use of compressors! :) 

To the matter: When the installer shows the window "Who are you?", and asks for a username and psswd, etc, there are also some choices:
> automatic session login [COLOR="Red"]<-- the one you want
[/COLOR]ask password to session login
encrypt your home partition

Just in case you've overseen it...
Cheers
JC

---

