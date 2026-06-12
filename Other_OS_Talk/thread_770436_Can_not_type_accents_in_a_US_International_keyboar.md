---
title: "Can not type accents in a US International keyboard using deadkeys in XFCE"
date: 2008-04-27
forum: Other OS Talk
---

### Post by tico on 2008-04-27
Hi,
I've installed Vector Linux (an XFCE based distro) in a virtual machine and spent the last days trying to setup my keyboard to type accents. No success. This is not a problem of Vector Linux, since I've tried another XFCE distro (Zenwalk) and I've had the same issue.
Here’s what I’ve done:
1. I’ve modified /etc/X11/xorg.conf:
Section "InputDevice"
   Identifier   "Keyboard0"
   Option      "XkbRules"   "xorg"
   Option      "XkbModel"   "pc105"
   Option      "XkbLayout"   "us"
   Option      "XkbVariant"   "intl"

2. I’ve changed the locale to en_US.UTF-8 editing files lang.csh and lang.sh in /etc/profile.d
3. I’ve done in terminal: export GTK_IM_MODULE=xim (and tried without this option too)

The problem is certainly in the deadkeys. They don’t work. I can type “ç” (cedilla) using alt+comma (as I do in Xubuntu), but if I type “acute” (it’s a deadkey in the international layout) + a, nothing happens. In Xubuntu I get “á”. I’ve changed "XkbLayout" from"us" to “pt” and deadkeys work, but it’s not a real solution, since they do not correspond to the deadkeys of my physical US keyboard (different layout). So the problem is the configuration of deadkeys in US international layout. I can type accents using a compose key, but it’s not a practical solution if you have to type a lot of accents. If I use a compose key, the keyboard types accents and system recognizes them (á, à, é, è, â, ê ã, õ, ñ). How could I fix this problem with deadkeys?
In Xubuntu (Ubuntu+XFCE) I don’t have this problem, since it has a special tab for “Layout” in “Keyboard Preferences” (Settings>Settings Manager>Keyboard) where I can add Layout: us Variant: intl. But XFCE in Vector doesn’t have this tab. It has only the following tabs: “Settings”, “Shortcuts”, “Accessibility”.

Does anybody can type accents in a US International keyboard using deadkeys? Any help is welcome. I’d like to use Vector in my laptop, but I need do fix this problem, otherwise I’ll not be able to do my work.
Thanks a lot.

---

### Post by cardinals_fan on 2008-04-27
Try adding the following line to your xorg.conf:
```

Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
Option "XkbVariant" "intl"
**Option "XkbOptions" "compose:rwin"**

```
It's working fine on my Zenwalk box.

---

### Post by tico on 2008-04-27
Thanks for your answer. Unfortunately, it doesn't work. Anyway, I wouldn't like to use "compose", since it's more complicated to type. I'd like to use deadkeys, but they don't work. 
I've just made a new Vector Linux install. I haven't changed anything. Here's my xorg.conf keyboard section:  
Section "InputDevice"
	Identifier	"Keyboard0"
	Driver		"kbd"
	Option		"XkbLayout"	"us"
	Option		"XkbModel"	""
	Option		"Xkbvariant"	""

I can't even type the English apostrophe (') symbol. It's simply impossible. It doesn't work, because it's a deadkey (even if the keyboard layout has no deadkeys). 

Any other idea?

Thanks again.

---

