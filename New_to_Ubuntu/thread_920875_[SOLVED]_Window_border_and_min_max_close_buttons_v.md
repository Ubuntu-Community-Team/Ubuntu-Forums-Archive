---
title: "[SOLVED] Window border and min max close buttons vanished"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by tradet on 2008-09-15
3rd day with ubuntu and now something moderately serious happened. My border around all windows has disappeared. You know the one that starts out as brown with a title ex. 'google blahblah' and away went the min max and close buttons.

I've been playing around in compiz and obviously I did something... Found this [thread]("http://ubuntuforums.org/showthread.php?t=835777&highlight=min+max+bar") where it said:

Are you running compiz. If so you need the line:
> Option "AddARGBGLXVisuals" "True"
put in the screen section of your xorg.conf file.

I'd love to try it.. but don't how where to find the xorg file.

---

### Post by houbysoft.xf.cz on 2008-09-15
> **tradet said:**
> 3rd day with ubuntu and now something moderately serious happened. My border around all windows has disappeared. You know the one that starts out as brown with a title ex. 'google blahblah' and away went the min max and close buttons.

I've been playing around in compiz and obviously I did something... Found this [thread]("http://ubuntuforums.org/showthread.php?t=835777&highlight=min+max+bar") where it said:

Are you running compiz. If so you need the line:

put in the screen section of your xorg.conf file.

I'd love to try it.. but don't how where to find the xorg file.

/etc/X11/xorg.conf

---

### Post by perlluver on 2008-09-15
> **tradet said:**
> 3rd day with ubuntu and now something moderately serious happened. My border around all windows has disappeared. You know the one that starts out as brown with a title ex. 'google blahblah' and away went the min max and close buttons.

I've been playing around in compiz and obviously I did something... Found this [thread]("http://ubuntuforums.org/showthread.php?t=835777&highlight=min+max+bar") where it said:

Are you running compiz. If so you need the line:

put in the screen section of your xorg.conf file.

I'd love to try it.. but don't how where to find the xorg file.

Your xorg is located /etc/X11/xorg.conf, also before that try, alt+f2 and enter this code ```
gtk-window-decorator --replace
```.

---

### Post by tradet on 2008-09-15
That was fast!

Worked with:
> gtk-window-decorator --replace

Thanks :)

---

### Post by perlluver on 2008-09-15
> **tradet said:**
> That was fast!

Worked with:


Thanks :)

Also if you have emerald installed, you would use emerald --replace.

---

