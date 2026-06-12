---
title: "[SOLVED] Remove ubuntu icon and replace with original gnome panel icon"
date: 2005-10-13
forum: Outdated Tutorials &amp; Tips
---

### Post by manicka on 2005-10-13
I know lots of people will like the ubuntu icon on the menu bar, but if you're like me and like the old foot, here's how to get it back.
```

sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.bak
killall gnome-panel
```

If you change your mind and want the ubuntu icon back

```
sudo mv /usr/share/icons/hicolor/48x48/apps/distributor-logo.png.bak /usr/share/icons/hicolor/48x48/apps/distributor-logo.png
killall gnome-panel
```

---

### Post by kudu on 2005-10-14
Yes...THANK YOU! Exactly what I was looking for.

kudu

---

### Post by kudu on 2005-10-14
And would you be knowing how to get rid of the boot-up splash screen and change the login splash screen back to the way things were in Hoary ? I can't see the boot-up messages on the new dinky little text area, much prefer the Hoary message screen. Nice big white letters with red when something goes haywire.

regards,
kudu

---

### Post by blu.gecko on 2005-10-21
Sweet mother of jesus, that was my biggest ack with 5.10 other than that they did a world of good on the new version.

many thanks,

blu.gecko:D

---

### Post by soul_rebel on 2005-10-22
does not work for me...

---

### Post by blu.gecko on 2005-10-22
[QUOTE=soul_rebel]does not work for me...[/QUOTE]

even after the reboot??:rolleyes:

---

### Post by soul_rebel on 2005-10-23
yes really.
I also tryed to do it in the "right and clean way" using the config database editor and still does not work.

---

### Post by Kyral on 2005-10-24
Yanno what the most ironic thing about this topic is?

Back in 5.04, changing the Foot Icon to the Ubuntu Logo was one of the most liked tricks you could do ;P

---

### Post by manicka on 2005-10-24
Horses for courses :)

---

### Post by kewler on 2005-10-25
what _IS_ that thing that replaced my icon?! I thought it was going to be a foot!

---

### Post by kewler on 2005-10-25
oops. nevermind, it was just part of the theme :p

---

### Post by blu.gecko on 2005-10-25
ROTFL.....that funny.....wtf...oh nevermind....LOL

good humor

---

### Post by Nu-Buntu on 2005-11-23
It looks like an armadillo to me.

---

### Post by ticlo on 2006-03-12
Saving a 48x48 pixel PNG as **~/.icons/hicolor/48x48/apps/distributor-logo.png** will have the same effect, but it won't affect other users. :)

(**killall gnome-panel** is still needed)

---

### Post by FISHERMAN on 2006-04-21
I've just reinstalled Ubuntu Breezy and this no longer works.
What should I do ?
I' ve tried everything.

---

### Post by domino on 2006-04-23
Don't work with Dapper Beta either :)

---

### Post by bluefuse on 2006-09-18
here is a reference, but it did not work for me.

[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](*](http://doc.gwos.org/index.php/Gnome_Icon_Dapper](*),)

---

### Post by Syntax_Err on 2011-01-23
Copy your image to /usr/share/icons/YourIconTheme/24x24/start-here.png

Then run as root 'gtk-update-icon-cache /usr/share/icons/YourIconTheme/'
:popcorn:

---

