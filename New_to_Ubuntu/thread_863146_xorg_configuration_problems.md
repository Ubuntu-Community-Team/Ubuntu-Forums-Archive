---
title: "xorg configuration problems"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by kathrync on 2008-07-18
Hi

I have been trying to run an old game through Wine.  In order to make it work, I had to go run dpkg-reconfigure xserver-xorg and enable the kernel framebuffering device (or whatever it is called) to allow the game to change the screen resolution.

Two problems:

Firstly, this change works, but for some reason it won't save so I have to re-do it every time I start the computer.

Secondly, since doing this, my keyboard setting has changed from a UK layout to a US layout, which is annoying because I can't find all the symbols!  I am sure I didn't touch the keyboard settings, but I guess I must have as I can't think of anything else that would have made this change.  I can't seem to make it change back though....any ideas?

Thanks

Kathryn

---

### Post by schauerlich on 2008-07-18
Reconfiguring your xorg.conf will also reset your keyboard settings.

---

### Post by kathrync on 2008-07-18
Yes, I had sort of gathered that!  I think I was careful not to change anything though.  Any idea what I need to do to change it back?  The obvious thing is to change the country, but this is already set to UK, so I have obviously changed something else.

Anyone have any ideas on why my original change won't save?

---

### Post by houbysoft.xf.cz on 2008-07-18
Huh, I think the simplest way is to edit xorg.conf. So, try ALT+F2, then type "gksu gedit /etc/X11/xorg.conf" (replace gedit with any other editor you like), and then edit the part of the file that looks like this :

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection
```

Then edit the "Option  "XkbLayout" "us"" as it is in my file to "Option  "XkbLayout" "uk"", so that the section looks like this in the end:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection
```

Then save the file, and you will have your old kb layout. Btw, you will maybe have to restart Xserver (or your computer). I'm not sure :)

---

### Post by kathrync on 2008-07-18
Ok, keyboard issue is now sorted.  Now I just have to work out how to make the frame buffering thingy stop defaulting back to being off....

Thoughts?

---

