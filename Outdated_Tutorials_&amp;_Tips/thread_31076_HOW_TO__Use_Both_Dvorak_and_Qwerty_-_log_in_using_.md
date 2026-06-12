---
title: "HOW TO:  Use Both Dvorak and Qwerty - log in using either"
date: 2005-05-01
forum: Outdated Tutorials &amp; Tips
---

### Post by graigsmith on 2005-05-01
this requires editing your xorg.conf file.  after you do this, you will be able to log into gnome using EITHER qwerty or dvorak :)

you will probably already have this option

	Option		"XkbLayout"     "dvorak"     OR
	Option		"XkbLayout"     "us"

change it to this. 

	Option		"XkbLayout"     "dvorak,us"
	Option 		"XkbOptions"   "grp:shift_toggle"

Once you do that, restart x using ctrl-alt-backspace.. now when the gnome login screen comes up, you can hit both shift keys to change keyboard layouts.  that way anyone who doesn't know dvorak, can still log into your computer, without the stress of trying to figure out how to type their name. :)

---

### Post by Domhnull on 2005-05-01
Thanks, I was able to use dvorak fine once logged in but didn't know how to change it so it was dvorak on the login screen.

---

### Post by N'Jal on 2005-05-01
Are you using Warty coz i had this problem on warty where QWERTY was used by default and i didn't know how to alter it. However since upgrading to hoary i have been able to use DVORAK at the login prompt fine.

It's this and having to use QWERTY at college that my brain is trained to use both layouts >_<

Not good not good not good

---

### Post by graigsmith on 2005-05-01
N'jal, nope im using hoary.

---

### Post by Domhnull on 2005-05-02
Also on Hoary, but the edit worked just great.  I did get a message after rebooting that my x and gnome settings were different and it asked which I wanted to use.  But it works great.

---

### Post by graigsmith on 2005-05-02
[QUOTE=Domhnull]Also on Hoary, but the edit worked just great.  I did get a message after rebooting that my x and gnome settings were different and it asked which I wanted to use.  But it works great.[/QUOTE]
 oh yeah, just pick use gnome settings. and dont ask this question again.  and it never pops up again.

---

### Post by hanzj on 2005-10-16
[QUOTE=graigsmith]
	Option 		"XkbOptions"   "grp:shift_toggle"
[/QUOTE]

Graig, where'd you learn about this **shift_toggle** thingy?

---

### Post by Robtastic84 on 2006-10-20
Is there a way to do this once in ubuntu. Its nice to have it at the log in screen but in the OS would be way better.

---

### Post by total wormage on 2006-10-20
thanks a lot! i always had to think really hard to get my password correct using qwerty on a dvorak keyboard, this helps! :biggrin:

---

### Post by alexmoon on 2007-09-29
I accidentally picked "x settings" instead of gnome settings, and now it doesn't seem to be working. How can I reverse this?

(Also: thanks for the advice, it's been really useful for me. I use it for flipping between dvorak and a greek layout for greek lessons. Only problem is that my greek keyboard disappeared and now I can't get it back - whenever I press the shift keys...nothing happens, it just stays in dvorak.)

---

### Post by carloslosgrande on 2007-12-13
[FONT="Comic Sans MS"]Just saw this, works great! Thanks Craigsmith:)[/FONT]

---

