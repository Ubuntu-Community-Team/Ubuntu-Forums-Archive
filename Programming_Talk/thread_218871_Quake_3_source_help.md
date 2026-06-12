---
title: "Quake 3 source help"
date: 2006-07-19
forum: Programming Talk
---

### Post by goobers on 2006-07-19
Hey, I was wondering if anyone here has had any experience with the Q3 source code, cos i'm trying to figure out how to change rate of fire for the machine gun and its driving me crazy :p

---

### Post by MrHorus on 2006-07-19
> **goobers said:**
> Hey, I was wondering if anyone here has had any experience with the Q3 source code, cos i'm trying to figure out how to change rate of fire for the machine gun and its driving me crazy :p

There is code somewhere that defines all the weapons and there attributes, including the rate of fire.

I remember doing something similar a few years ago with the Quake 2 source.

---

### Post by goobers on 2006-07-19
I found the weapon attributes, such as damage per bullet etc, but not one specifically for firerate...

I dunno if i'm being stupid or something:p

---

### Post by jmoral on 2007-07-16
Took me a while to find it, too.  The source file that controls fire rate is:

code/game/bg_pmove.c,  line 1648

```

...
	case WP_ROCKET_LAUNCHER:
		addTime = 800;
		break;
	case WP_PLASMAGUN:
		addTime = 100;
		break;
	case WP_RAILGUN:
		addTime = 1500;
		break;
	case WP_BFG:
		addTime = 200;
		break;
...

```

addTime is the delay in ms between shots, so decreasing addTime increases the rate of fire.

---

