---
title: "ATI hd 2400 pro help!"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by copper103 on 2008-06-29
hello unfortunately my hd 2400 pro doesnt seem to be working with ubuntu, this is bad as anything 3d turns into a slideshow. the card is detected, but it just doesnt seem to be doing anything. I urgently need help as my computer is functioning very slow. :confused:

---

### Post by Methuselah on 2008-06-29
Are you sure that 3D acceleration is enabled?

Try the below in a terminal to find out:

```

glxinfo | grep "direct rendering"

```

The output will probably be 'No' which will mean that all 3D rendering is being done by the CPU hence the slowness.

Homestly, I doubt this card will be supported by the free drivers currently in Ubuntu and I can't really recommend the ATI driver. I tried it once, against my better judgement, and my computer would reboot every time I tried to log in.

---

