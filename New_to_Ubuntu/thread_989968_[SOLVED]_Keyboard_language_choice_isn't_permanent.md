---
title: "[SOLVED] Keyboard language choice isn't permanent"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by AlexOslo on 2008-11-22
I am running version 8.04 and have changed my keyboard setting from Danish (which I deleted) to Norwegian. It works fine for that session, but when I reboot it is back to Danish again.

Is there anything I've missed here?

Best regards,
Alex

---

### Post by Piraja on 2008-11-22
Sounds odd... It should be a persistent change (if you're not using LiveCD). Did you change the keyboard layout via System > Preferences > Keyboard as in the attached screenshot? (My kb layout is "Finland", while I prefer to use English as the system language.)

---

### Post by AlexOslo on 2008-11-22
> **Piraja said:**
> Sounds odd... It should be a persistent change (if you're not using LiveCD). Did you change the keyboard layout via System > Preferences > Keyboard as in the attached screenshot? (My kb layout is "Finland", while I prefer to use English as the system language.)

That's the screenshot I see, yes. I'm not using the Live CD. I'll check for certain again this evening.

---

### Post by unutbu on 2008-11-22
Open a terminal (Applications>Accessories>Terminal) and type

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20081122    # make a backup

gksu gedit /etc/X11/xorg.conf
```

Search for a 'XkbLayout'. Ignore any line that begins with a #. Those are comments.

If you see
```

    Option         "XkbLayout" "dk"
```

change it to```


    Option         "XkbLayout" "no"
```

Save and exit gedit.
Log out.
Log back in to make the change take effect.

---

### Post by AlexOslo on 2008-11-22
> **unutbu said:**
> Open a terminal (Applications>Accessories>Terminal) and type

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20081122    # make a backup

gksu gedit /etc/X11/xorg.conf
```

Search for a 'XkbLayout'. Ignore any line that begins with a #. Those are comments.

If you see
```

    Option         "XkbLayout" "dk"
```

change it to```


    Option         "XkbLayout" "no"
```

Save and exit gedit.
Log out.
Log back in to make the change take effect.

This was super, Unutbu: right on! 
I was a bit confused with your writing this:

```
 cp /etc/X11/xorg.conf /etc/X11/xorg.conf-20081122    # make a backup 
```

but quickly realized it was redundant, and just typed

```
 gksu gedit /etc/X11/xorg.conf 
```

and followed your instructions.

Thanks a Bunch.

Alex

"Be generous in prosperity, and thankful in adversity." - Baha'i writings

---

