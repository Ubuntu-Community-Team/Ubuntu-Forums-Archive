---
title: "Keyboard 3rd Level Options don't stay on"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by anthropoidster on 2008-05-28
I'm having a small but annoying problem with my keyboard layout options in Hardy on my Desktop.  Every time I startup, the keyboard acts like the 3rd level options are turned off even though they are not.  In every session I have to go to Preferences - Keyboard - Layout - Layout Options - Third Level Choosers and then uncheck and then check again my chosen option (Press any WIN key).  For the rest of the session everything is fine, but the next time I startup, the keyboard again acts like the Third Level Chooser is turned off even though it shows that it is checked.  The Keyboard model is Generic 105 key (Intl) PC and the Layout is USA International (with dead keys).  However, my xorg.conf shows:

Section "InputDevice"
	Identifier		"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"

I think this may be where my problem is, but I'm not sure how it should be adjusted or if it is indeed the problem.

Looking for more of that ever helpful forum wisdom.

---

### Post by vautrin44 on 2009-02-04
I had the same problem; couldn't find an elegant way to solve it so I did the following:

Non-elegant solution

Reinstall Ubuntu Hardy.
Select USA International(with dead keys)as the default keyboard.
In the first boot up, I changed the 3rd level choosers.
Opened OpenOffice to check; 3rd level choosers were working.
Restart the computer.
Open OpenOffice and check if the 3rd level choosers are still working the way I set them up


Until someone comes up with an elegant solution to this problem, try this solution.

---

### Post by anthropoidster on 2009-02-04
Thanks for coming back on this thread - I thought it was dead.

At some point after posting my question, I added a couple lines to my xorg.conf so that it now looks like this...

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbVariant" "intl"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Everything's been fine since.

---

### Post by vautrin44 on 2009-02-12
Thanks a lot. I´ll try your solution.

Regarding mine, it was _wrong_. I was using the Ubuntu login screen, and everything was fine. However, I changed my computer so automatic login and my custom third level choosers were disabled. I changed the computer again so that I used the login screen, and the third level choosers were functioning well again.

It seems that, as it is, Ubuntu needs you to login manually for it to use the custom third level choosers. So no reinstall may be needed, just manual login, unless we use your solution.

---

