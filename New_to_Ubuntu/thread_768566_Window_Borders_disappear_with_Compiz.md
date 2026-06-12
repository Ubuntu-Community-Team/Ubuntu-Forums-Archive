---
title: "Window Borders disappear with Compiz"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by cybertron3000 on 2008-04-26
I upgraded to the 8.04 Hardy Heron.  I works/looks perfectly without any extra graphical effects, "but"... 

The only noticeable difference now is that when I try to use the Compiz effects [i.e. trying to use "normal" or "extra" on visual effects in Appearance menu], my window borders disappear (aka the titlebar at top of each window).

Furthermore, the Emerald program simply cannot be applied as it did before in Gutsy.

Any ideas out there to solve this minor issue?

---

### Post by SpaceMonk3y on 2008-04-26
Encountering the same problem with Emerald on my machine.  Compiz is working correctly though.

I have attempted a reinstall of Emerald, and did the 'emerald --replace' in terminal.  All that did was erased all my window borders.

---

### Post by romeozor on 2008-04-26
iirc you need to enable a certain desktop effect to get it right. its not in front of me right now so i'm just guessing its called "window decorations"

---

### Post by c4v3m4n on 2008-04-26
You need windows decorations to be enabled first.  Check if a compiz plugin called "reflection" is enabled.  When that's enabled i cant see any of my window decorations.

---

### Post by hariprs on 2008-04-26
It happened once for me also. But after a restart it was fine. Did you try restarting?

---

### Post by c4v3m4n on 2008-04-27
Did you get this fixed yet?

---

### Post by Gazneth on 2008-04-28
I got emerald to work by going to compizconfig, effects, window decoration, in that menu where the command line is erase what is written then enter:```
emerald --replace &
``` Enter the same in a terminal to start emerald. Then logout and back in to check if it worked.

---

