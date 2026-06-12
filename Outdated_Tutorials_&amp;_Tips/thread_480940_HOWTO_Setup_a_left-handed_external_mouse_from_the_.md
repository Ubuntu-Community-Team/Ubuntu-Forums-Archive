---
title: "HOWTO: Setup a left-handed external mouse from the command-line"
date: 2007-06-21
forum: Outdated Tutorials &amp; Tips
---

### Post by mustali on 2007-06-21
This one's for my left-handed comrades.

I use Ubuntu on my laptop and find it annoying that Ubuntu does not offer an independent configuration for mouse buttons on the external mouse. I would like to keep the mousepad buttons right-handed while the *external* mouse left-handed with the primary and secondary buttons swapped.

The following command switches the left and right buttons on an *external* mouse connected to a laptop.
```

xmodmap -e "pointer = 3 2 1"

```

To restore the setting:
```

xmodmap -e "pointer = default"

```


xmodmap is capable of modifying several button mappings. check it out.

---

### Post by kobewan on 2007-06-22
Nice find, but how do you specify if it changes on your external or internal mouse? If I remember correctly, xmodmap would only change my internal mouse's buttons.

---

### Post by mustali on 2007-06-22
The xmodmap arguments I used above have no effect on my internal mouse. "321" and "default" leave the mouse set to right handed. I am running Fiesty with GNOME.

There must be a some other option to specify the internal mouse.

---

