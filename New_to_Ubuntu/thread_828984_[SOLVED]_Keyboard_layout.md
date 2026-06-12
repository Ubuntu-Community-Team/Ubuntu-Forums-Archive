---
title: "[SOLVED] Keyboard layout"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by RobHK on 2008-06-14
When I boot, the keyboard layout is wrong. I am in the UK with a UK keyboard. The characters are all OK but other keys are wrong. For example "/" comes out as "-"

If I open Keyboard Preferences/layout the UK keyboard is the only one there, but if I click "Reset defaults", "Spain" appears and UK disappears. I then manually add UK, remove Spain, and close. The UK keyboard now works. But when I shut down and reboot the setup has not saved. I am back to where I started.

EDIT

Now resolved after Googling. I had earlier had to import a different xorg.conf to get the video driver working properly. The xorg.conf I imported had *Option "XkbLayout" "es". *


I fixed this by editing /etc/X11/xorg.conf and changing

Option "XkbLayout" "es"

to

Option "XkbLayout" "uk"

---

### Post by anthropoidster on 2008-06-14
I had a very similar problem here - [http://ubuntuforums.org/showthread.php?t=810372](http://ubuntuforums.org/showthread.php?t=810372) - and while I received no reply, I did figure it out and the problem was indeed the original xorg.conf file which was created when that OS was installed.  As I have multiple installations, I was able to track down the problem by finding one of the OS's that worked the way I wanted it and then compare files. In order to get my keyboard to stick where I wanted it, I had to change the following lines:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"

to:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"

It's been perfect ever since. I don't know the specific code for the keyboard setup you want, but I'm pretty sure that your problem lies here.

Hope this helps.

---

### Post by RobHK on 2008-06-14
> **anthropoidster said:**
> I had a very similar problem here - [http://ubuntuforums.org/showthread.php?t=810372](http://ubuntuforums.org/showthread.php?t=810372) - and while I received no reply, I did figure it out and the problem was indeed the original xorg.conf file which was created when that OS was installed.  As I have multiple installations, I was able to track down the problem by finding one of the OS's that worked the way I wanted it and then compare files. In order to get my keyboard to stick where I wanted it, I had to change the following lines:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"

to:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbVariant"	"intl"
	Option		"XkbOptions"	"lv3:ralt_switch"

It's been perfect ever since. I don't know the specific code for the keyboard setup you want, but I'm pretty sure that your problem lies here.

Hope this helps.

Thanks very much. As you'll see from the edit in my post I found the same solution as you. :)

---

