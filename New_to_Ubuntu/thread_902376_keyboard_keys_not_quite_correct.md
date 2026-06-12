---
title: "keyboard keys not quite correct"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-08-27
I have a laptop with a DE (german) keyboard layout.
I seem to get all the extended letters OK but some of the other keys are not representing their displayed characters.
I had this working OK before but had some display issues and after the fix, I discovered the keys were different.

I remember a DOS looking dialogue that I had to go through to solve the display issue and in it were alot of questions about the keyboard. I think that his where I screwed it up.
Since then I discovered the xorg.conf and thought that editing this file is the trick.

Here is how it stands at the moment.

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"[COLOR="Red"]pc101[/COLOR]"
	Option		"XkbLayout"	"de"
	Option		"XkbVariant"	"nodeadkeys"
EndSection
```

But it seems that changing the XkbModel attribute makes no difference. I have tried 102 and 103 and rebooted every time I changed it, but it made no difference.

Can anyone help me out here please?

---

### Post by philinux on 2008-08-27
Try

System>Prefs>Keyboard

---

### Post by howlingmadhowie on 2008-08-27
you probably have a pc105 keyboard, at least that's what i use for my german keyboards.


edit----------------

btw, you don't have to restart every time you change /etc/X11/xorg.conf, you just have to restart X. you can do this by logging out.

---

### Post by philinux on 2008-08-27
```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"

```

This is my snip of xorg.

---

### Post by steinzeitmensch on 2008-08-27
I have now tried 101, 102, and 105 for the XkbModel attribute.
Each time I changed the xorg.conf file I restart (even though I may not have to) just to be sure, and each of these settings seem to have had no effect on the keyboard.
Am I doing something wrong here?

---

### Post by philinux on 2008-08-27
Did you try

System>Prefs>Keyboard >  Layouts Tab

---

### Post by northern lights on 2008-08-27
From the shell run ```
sudo dpkg-reconfigure xserver-xorg
```you will be prompted with several dialogs, most of which are keyboard related. Answer to the best of your knowledge.



P.S.
+1 for PC105 for German keyboards.

---

### Post by steinzeitmensch on 2008-08-27
> Did you try

System>Prefs>Keyboard > Layouts Tab

Yes tried this and played with alot of different keyboards, but the laptop I haved is a Lenovo 3000 N200 and Lenovo is not in the list of generic keyboards. I know that the keyboard has probably not changed since the days of IBM (since that was arguably the best part of the thinkpad laptops and Lenovo recognised this), but all the IBM keyboards actually made no difference to the current settings.
Strange.

---

