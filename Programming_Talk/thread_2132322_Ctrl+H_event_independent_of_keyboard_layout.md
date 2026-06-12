---
title: "Ctrl+H event independent of keyboard layout"
date: 2013-04-04
forum: Programming Talk
---

### Post by bird1500 on 2013-04-04
Hi,
examining the "keyval" field of a GdkEventKey struct doesn't work cause it only works if the user's using a Latin (English-like) keyboard layout.
So, Ctrl+H works in "English US" mode but fails say with a "Russian" keyboard layout.

Since I need to catch a Ctrl+H event regardless of keyboard layout I went with the "hardware_keycode" field of the GdkEventKey struct
which always reports "43" for the "H" key on the keyboard regardless of keyboard layout.

The question is, is there a better approach? And does "43" stand for the "H" key on every keyboard or just mine (Logitech)?

---

### Post by schragge on 2013-04-04
> **bird1500 said:**
> does "43" stand for the "H" key on every keyboard or just mine (Logitech)?
```

[COLOR=green]$[/COLOR] grep -r '\<43;$' /usr/share/X11/xkb/keycodes
[COLOR=green]/usr/share/X11/xkb/keycodes/sony:    <AD10> = 43;
/usr/share/X11/xkb/keycodes/amiga:    <AC04> = 43;
/usr/share/X11/xkb/keycodes/amiga:    <AC04> = 43;
/usr/share/X11/xkb/keycodes/ibm:    <AC05> = 43;
/usr/share/X11/xkb/keycodes/digital_vndr/pc:    <AC04>  = 43;
/usr/share/X11/xkb/keycodes/sun:    <AE07> = 43;
/usr/share/X11/xkb/keycodes/sun:    <AE07> = 43;
/usr/share/X11/xkb/keycodes/sun:    <AE07> = 43;
/usr/share/X11/xkb/keycodes/sun:    <AE07> = 43;
/usr/share/X11/xkb/keycodes/sun:    <AE07> = 43;
/usr/share/X11/xkb/keycodes/xfree98:    <AC07> =  43;
/usr/share/X11/xkb/keycodes/evdev:      <AC06> = 43;
/usr/share/X11/xkb/keycodes/hp:    <AB02> = 43;
/usr/share/X11/xkb/keycodes/hp:    <FK11> = 43;
/usr/share/X11/xkb/keycodes/fujitsu:    <AE06> = 43;
/usr/share/X11/xkb/keycodes/sgi_vndr/indigo:    <AB05> = 43;
/usr/share/X11/xkb/keycodes/sgi_vndr/indy:    <AC03> = 43;
/usr/share/X11/xkb/keycodes/ataritt:    <AC06> =  43;
/usr/share/X11/xkb/keycodes/xfree86:    <AC06> =  43;
/usr/share/X11/xkb/keycodes/macintosh:    <AD10> = 43;
$[/COLOR] grep -r '<AC06>[ \t]=[ \t]*43;$' /usr/share/X11/xkb/keycodes
[COLOR=green]/usr/share/X11/xkb/keycodes/evdev:      <AC06> = 43;
/usr/share/X11/xkb/keycodes/ataritt:    <AC06> =  43;
/usr/share/X11/xkb/keycodes/xfree86:    <AC06> =  43;[/COLOR]

```

---

### Post by conradin on 2013-04-05
This do anything for you?
[http://stackoverflow.com/questions/2767126/how-to-detect-that-ctrlr-was-pressed](http://stackoverflow.com/questions/2767126/how-to-detect-that-ctrlr-was-pressed)

---

### Post by schragge on 2013-04-05
I'm afraid no. The linked question is about [jQuery](http://en.wikipedia.org/wiki/JQuery). The OP asked about [GDK](http://en.wikipedia.org/wiki/GDK).

---

