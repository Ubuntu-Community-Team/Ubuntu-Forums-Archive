---
title: "how do i wrap a gui arround a command line program?"
date: 2007-02-01
forum: Programming Talk
---

### Post by Choad on 2007-02-01
just for an exercise in learning gtk and whatnot, im going to be making a gtk gui for the popstation iso converter

it converts playstation 1 game iso's to be playable on the psp :)

im using anjuta for the moment, can someone help me out. point me in the right direction etc.

---

### Post by Tomosaur on 2007-02-01
You don't really 'wrap it around' a CLI program (although you can, it's just not the easiest way). What you would do is create the GUI itself, and allow a user to configure their options (ie, filename, burn speed etc etc etc). You then parse all of these options into a string and just call the iso converter as you would on the command line, using the system() function in stdlib.

---

### Post by Choad on 2007-02-01
aha! cunning :)

stdlib you say....

---

### Post by Choad on 2007-02-01
```
#include <stdlib.h>

int main() {
	system("gksudo nautilus");
	return 0;
	}
```

well well, it works!

---

### Post by 3rdalbum on 2007-02-01
If you want to look at some GUI frontends I'm writing in Python, check out the [Copland]("http://code.google.com/p/coplandppc/") wiki. The source code is actually on the wiki (Python and Pythoncard)

---

### Post by Tomosaur on 2007-02-02
> **Choad said:**
> ```
#include <stdlib.h>

int main() {
	system("gksudo nautilus");
	return 0;
	}
```

well well, it works!

Yup :P

---

### Post by 23meg on 2007-02-02
Would it be possible to do this in the same way wih FreePascal?

---

### Post by Keith Hedger on 2007-06-07
If you're using gnome you should use the glib API's to spawn proccesses it gives you more control, and allows you to send data/recieve data via stdin/sdout and also get informed when the app dies you can also run the external app synchronisly or asyncrinously, you might want to install DevHelp (its in the repos) and serach for g_spawn_ 

Good luck!

---

