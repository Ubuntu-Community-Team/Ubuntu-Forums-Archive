---
title: "GNOME is Broken"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by RATM_Owns on 2008-09-09
Basically, I went into my default GNOME session and it was broken. The desktop was a black box. There was a white box where Conky was supposed to be and the AWN dock at the bottom was also messed up.

And when I booted into another session and ran Nautilus from terminal, I got this error:
```
nautilus: symbol lookup error: nautilus: undefined symbol: g_file_query_filesystem_info_async
```

I was also looking around in Google once it stopped working and I found this link:
[http://ubuntuforums.org/showthread.php?t=770191](http://ubuntuforums.org/showthread.php?t=770191)

But
```
locate glocalfile.c
```
brought up nothing.

---

### Post by LowSky on 2008-09-09
have you tried using metacity instead of compiz/awn?

have you tried reinstalling nautilus

---

### Post by RATM_Owns on 2008-09-09
Reinstalling Nautilus, yes.

Using Metacity instead of Compiz/AWN, I'm too idiotic to know how.

---

### Post by LowSky on 2008-09-09
in terminal type

```
metacity --replace
```

also try removing Conky and AWN then reinstalling

---

### Post by RATM_Owns on 2008-09-09
> **LowSky said:**
> in terminal type

```
metacity --replace
```also try removing Conky and AWN then reinstalling
Wait, doesn't metacity --replace replace the current manager?

Which means I'd need to type it in GNOME?

But I'll try it in Failsafe Terminal then GNOME.

---

### Post by WRDN on 2008-09-09
At the login screen, press Ctrl, Alt and F1, then login from the shell prompt.
Now, you can reset gnome by typing:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Now, login normally and the settings will have been reset.

---

### Post by RATM_Owns on 2008-09-09
That only broke things more. xP

---

