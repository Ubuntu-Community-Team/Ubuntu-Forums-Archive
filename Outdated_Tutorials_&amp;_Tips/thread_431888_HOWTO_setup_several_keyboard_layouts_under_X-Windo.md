---
title: "HOWTO: setup several keyboard layouts under X-Window"
date: 2007-05-03
forum: Outdated Tutorials &amp; Tips
---

### Post by ilia on 2007-05-03
This guide describes how to set up multiple keyboard layouts under X-Window. Independent of the Desktop Environment (KDE/Gnome/Xfce/etc.). It was primary written for KDE users, but others may find it useful as well. This setup has several advantages over the KDE-only keyboard configuration, which you may set up through kcontrol. It also was the only way for me to be able to type Hebrew under wine, so may be useful with other languages/apps.

[LIST]
[*] find correct XkbOptions:
	[LIST]
	[*] decide how do you want to switch layouts (in X-Window it's called "change groups"). 
	[*] go to kcontrol->Keyboard Layout
	[*] go to the 3rd tab ("Xkb options"), check "Enable xkb options" and make the appropriate changes (check/uncheck). For example, if you want to switch with Alt+Shift make sure that only "Alt+Shift changes group." is checked.
	[*] look at the "Command:" textbox at the buttom of the tab and note the command. In our example it will be "setxkbmap -option grp:alt_shift_toggle"
	[*] copy or write down, what appears after "-option" word. In our example it will be "grp:alt_shift_toggle"
	[/LIST]
[*] disable KDE's keyboard layout switching:
	[LIST]
	[*] go to kcontrol->Keyboard Layout
	[*] on the first tab ("Layout") uncheck "Enable keyboard layouts" 
	[*] on the third tab ("Xkb Options") uncheck "Enable xkb options"
	[*] save changes :)
	[/LIST]
[*] edit /etc/X11/xorg.conf:
	[LIST]
	[*] find "InputDevice" section of the keyboard. It should contain 'Driver  "kbd"' line. For example:
		```

		Section "InputDevice"
			Identifier      "Generic Keyboard"
			Driver          "kbd"
			Option          "CoreKeyboard"
			Option          "XkbRules"      "xorg"
			Option          "XkbModel"      "pc104"
			Option          "XkbLayout"     "us"
		EndSection
		
```
	[*] change the section to reflect your preferences. Change "XkbLayout" option and add "XkbOptions" option with the value you've copied/written earlier from the kcontrol window. For example:
		```

		Section "InputDevice"
			Identifier      "Generic Keyboard"
			Driver          "kbd"
			Option          "CoreKeyboard"
			Option          "XkbRules"      "xorg"
			Option          "XkbModel"      "pc104"
			Option          "XkbLayout"     "us,ru,il"
			Option          "XkbOptions"    "grp:alt_shift_toggle"
		EndSection
		
```
	[*] save the file :)
	[/LIST]
[*] restart X-Window (end current KDE session and then press Ctrl+Alt+Backspace) and start KDE again
[*] setting keyboard layout indicator:
	[LIST]
	[*] instal kkbswitch package:
		sudo apt-get install kkbswitch
	[*] run kkbswitch
	[*] notice a new icon in the tray (it displays "1"). Right-click it and choose "Configure Keyboard Switch"
	[*] change icons for all your layouts
	[*] assure "Autostart" is checked
	[/LIST]
[/LIST]

In addition kkbswitch allows you to have per-window layout and switch between two "active" layouts instead of cycle through all (useful for 3 and more layouts).

Good luck!

---

### Post by El Viejo Lobo on 2007-05-09
Ilia, I was looking for "How to start kde after install it from: [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)
[B] How to install KDE

    * Read #General Notes
    * Read #How to add extra repositories
    * You may also look at some KDE Screenshots 

sudo aptitude install kubuntu-desktop

    Note: This installation will require ~400MB of disk space 

    * System -> Quit -> Log Out
    * To log in to KDE click on Sessions and choose KDE 

[edit]
[/B]
I can not log in to KDE with the instructions written above.  I found your thread  
which I am not sure it is what I need. I need to log in to KDE and I will be happy to be able to use Hebrew keyboard together with English and Spanish which are my working languages. I hope that you can help me on this two issues.
Toda.

---

### Post by ilia on 2007-05-11
> **El Viejo Lobo said:**
> I can not log in to KDE with the instructions written above.  I found your thread which I am not sure it is what I need. I need to log in to KDE and I will be happy to be able to use Hebrew keyboard together with English and Spanish which are my working languages. I hope that you can help me on this two issues.
Hi, my post is about installing multilanguage keyboard, not about installing KDE. If you have problems installing KDE we can discuss it in another thread (you are welcome to create one). If the problems related to my original post, please describe what do you mean by "I can not log in to KDE".

---

### Post by El Viejo Lobo on 2007-05-11
I am sorry for misunderstanding your thread. I made a mass in my box trying to get KDE work by Synaptic in Ubuntu, I cleand up the mass reinstalling Feisy.
The Hebrew issue was what pooled my attention to your thread but I am not sure I undrstand your
idea about the keyboards. I have a second user in my box for Hebrew and it works accept that changing keyboards is a bit uncomfortable, "If I leave the Hebrew and log out I can not write the password to log in again. Is it possible to have it easier with your way? If yes, How can I do it with Ubuntu 7.04. Sorry for being so ignorant on all this Linux things, six month ago I did not know of it's existence at all. :confused: 
Thanks.

---

### Post by ©TriMoon® on 2007-05-11
I think that when you logout from your hebrew user the XWindows keyboard layout stays because it is switched by the XWindows system and not your login session.
Therefore to correct it you could try (1) or (2):
1) Manualy switch back to the layout you prefer / are able to enter your password using the "modifier key combination".
2) Press CTRL+ALT+BACKSPACE to restart your XServer prior to login. It will default to the "US" layout if you used the thread starters configuration...

If i wrote nonesense or something wrong, feel free to correct me...

---

### Post by der_joachim on 2007-05-12
Nice tip! Since I am using dvorak now, which my wife absolutely positively loathes (dvorak that is ;)). She prefers qwerty.  I was looking for a way to switch easily between keyboard layouts. I had already figured out the KDE part (which is IMHO pretty elegant), but the xorg part has been taken care of as well now. Thanks! Anyhoo, after some Googling I found out how to easily alternate between variants, so I thought I'd share:

```

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
    Option         "XkbOptions" "grp:alt_shift_toggle"
EndSection

```
Note the brackets.

---

### Post by ilia on 2007-05-13
> **El Viejo Lobo said:**
> If I leave the Hebrew and log out I can not write the password to log in again.
First of all, my configuration resolves this issue. Here is the explanation:

The problem arises due to the way, KDE handles multiple layouts. A standard X server (Xorg, XFree86) can handle several layouts and you can assign a key to tell X server to go to the next layout and to the previous. However, KDE does not relay on this functionality and when you configure multiple layouts in "KDE way", it uses only the first X-server layout and instead of telling X: "go to the next layout" it **replaces** the **current** layout with the next, you've configured in KDE. Therefore X server knows about only one layout all time. If you leave KDE you won't be able to switch the layout, and if the current one is non-latin you can't even enter your username. 
Pressing Ctrl-Alt-Backspace, as recommended by ©TriMoon®, restarts the X-server and therefore resets the layout to the default one, usually US-English. However, it is not a clever workaround and resembles the reboot operation that WIndows users perform every time something goes wrong...

In addition, by default KDE assigns Ctrl-Alt-K shortcut to switch the layout. So if you switch to any non-latin layout you can not switch back from it cause you just have no "K" sign to type. The only way is to switch with the tray icon (using a mouse) or to assign a different shortcut.

Therefore, my common recommendation to KDE newbies is to use KDE-way for switching keyboards as a last resort only.

---

### Post by karik on 2007-05-20
Hi!

I had followed the steps you stated in the post, however, have not got positive result. The keyboard layouts are still do not switch with hot keys. May be you know now about other solutions. By the way, I don't understand why there is an interface to setup keyboard switching, but in order to make the feature work you need to turn it off?

Thanks in advance for a feedback,
karik

---

### Post by ilia on 2007-05-21
> **karik said:**
> Hi!

I had followed the steps you stated in the post, however, have not got positive result. The keyboard layouts are still do not switch with hot keys.
Probably, you haven't followed the instructions exactly. Post your /etc/X11/xorg.conf and ~/.kde/share/config/kxkbrc files. We'll try to figure out.

>  May be you know now about other solutions. By the way, I don't understand why there is an interface to setup keyboard switching, but in order to make the feature work you need to turn it off?

Read my posts above for the explanation. There are two ways for you to have multiple layouts. Here we disable the "less preferred" one.

---

