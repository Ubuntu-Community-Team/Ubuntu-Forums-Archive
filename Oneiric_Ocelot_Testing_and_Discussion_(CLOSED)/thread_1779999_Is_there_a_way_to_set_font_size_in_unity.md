---
title: "Is there a way to set font size in unity?"
date: 2011-06-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mdurham on 2011-06-11
All prev. Ubuntus had a dialog for setting font size but I don't see one in Unity. Am I missing something or what?
Cheers, Mike

---

### Post by lucazade on 2011-06-11
> **mdurham said:**
> All prev. Ubuntus had a dialog for setting font size but I don't see one in Unity. Am I missing something or what?
Cheers, Mike

You have to use "gnome-tweak-tool" or "dconf-editor" to tune font settings.
Anyway is not related to Unity but to Gnome3 stack.

---

### Post by fjgaude on 2011-06-11
Yes, simply right click the desktop and you get a menu. Click 'Change Desktop Background' and then click 'Fonts'. There, you are home.

---

### Post by kostkon on 2011-06-11
Welcome to Gnome3. No font prefs by default :frown:

---

### Post by lucazade on 2011-06-11
> **fjgaude said:**
> Yes, simply right click the desktop and you get a menu. Click 'Change Desktop Background' and then click 'Fonts'. There, you are home.

You should have a special gnome3. :)

That option is no more present like it was in gnome2.

---

### Post by fjgaude on 2011-06-11
> **lucazade said:**
> You should have a special gnome3. :)

That option is no more present like it was in gnome2.

Are we not talking about Unity, not Gnome3?

---

### Post by kostkon on 2011-06-11
> **fjgaude said:**
> Are we not talking about Unity, not Gnome3?
We are talking about Unity with Gnome3 (unity in 11.10 is gnome3 based).

I believe you are referring to Gnome Shell; the fact is that Gnome3 != Gnome Shell.

Gnome Shell is a shell for Gnome3, like Unity.

---

### Post by arpanaut on 2011-06-11
> Are we not talking about Unity, not Gnome3?

We're talking Unity on OO which is quite broken right now a lot of functionality has not been brought to light yet.

Unity is a shell which sits on top of Gnome, be it gnome 2 in Natty and gnome 3 in Oneiric.
Gnome Shell is a shell which sit on top of gnome 3.  whole different thing.

Unity on top of gnome 3 is not as complete as it was in Natty. The transition to gnome 3 is not complete in Oneiric yet.

I'm sure others could explain it better, but that is my take.

---

### Post by Peter09 on 2011-06-11
Mmmm - I just tap the meta key, start typing 'appearance' and there is the application.

---

### Post by lucazade on 2011-06-11
> **Peter09 said:**
> Mmmm - I just tap the meta key, start typing 'appearance' and there is the application.

Which is an old refuse of gnome2 and it will be removed soon!

---

### Post by arpanaut on 2011-06-11
> **Peter09 said:**
> Mmmm - I just tap the meta key, start typing 'appearance' and there is the application.

been there, tried that, no workie in Oneiric for me...
No Appearance application on my install???

---

### Post by Mr. Picklesworth on 2011-06-11
I believe you will find a font size slider in the accessibility section of Control Centre. It is still possible to change the theme / font size, but there isn't a UI for it at the moment and someone should really make one.

---

### Post by Peter09 on 2011-06-11
try installing

gnome-appearance-properties 

thats the name of the application.

---

### Post by lucazade on 2011-06-11
> **Peter09 said:**
> try installing

gnome-appearance-properties 

thats the name of the application.

this change only the appearance of gnome2, so it is not a good suggestion.
gnome-appearance-properties is part of gnome2 and will be removed.

In gnome3 you can change settings via "dconf-editor" and via "gnome-tweak-tool"

[[IMG]http://dl.dropbox.com/u/1338581/varie/Schermatas.png[/IMG]]("http://dl.dropbox.com/u/1338581/varie/Schermata.png")

---

### Post by Peter09 on 2011-06-11
Apologies - I didn't realise that I'd dropped into the Oneiric forum, the user had simply stated - Unity -  and I had assumed he was talking about 11.04.

---

### Post by arpanaut on 2011-06-11
> **Peter09 said:**
> try installing

gnome-appearance-properties 

thats the name of the application.

Nothing with that name available on my Oneiric install...

> you will find a font size slider in the accessibility section of Control Centre

That's a global sizing, the fine grain sizing will have to be brought with a new gnome3 app. as you said.

Long way to go, short time to get there...
I wish the Devs the best of luck!

---

### Post by lucazade on 2011-06-11
> **Peter09 said:**
> Apologies - I didn't realise that I'd dropped into the Oneiric forum, the user had simply stated - Unity -  and I had assumed he was talking about 11.04.

Absolutely no problem! :)



I see btw there is still some confusion about gnome3 and gnome-shell, unfortunately, and I don't understand why.

GNOME Shell is just one part of GNOME 3. It (together with Mutter, the window managet) is its primary user interface. The secondary interface (for hardware that can't handle the 3D workload, or for people who don't care about glitz), is Gnome Panel + Metacity (old window manager), which will basically give you the look of current GNOME 2.

GNOME3 itself is a whole desktop suite that includes a whole bunch of stuff like a GUI toolkit, development suites, a file manager, some utilities, some system-level daemons, and a whole bunch of apps.

---

### Post by mdurham on 2011-06-12
> **lucazade said:**
> You have to use "gnome-tweak-tool" or "dconf-editor" to tune font settings.
Anyway is not related to Unity but to Gnome3 stack.

Thanks for the advice but, I can't find anything in "gnome-tweak" that will set font sizes and "dconf" doesn't appear to work.
I find it a bit amazing that an Alpha is released without a tool to adjust font size. Such a fundamental and essential thing. However...
Cheers, Mike

---

### Post by cariboo on 2011-06-12
> **mdurham said:**
> Thanks for the advice but, I can't find anything in "gnome-tweak" that will set font sizes and "dconf" doesn't appear to work.
I find it a bit amazing that an Alpha is released without a tool to adjust font size. Such a fundamental and essential thing. However...
Cheers, Mike

Have you got dconf-tools installed? The command to use the editor is:

```
dconf-editor
```

---

### Post by Mr. Picklesworth on 2011-06-12
> **mdurham said:**
> Thanks for the advice but, I can't find anything in "gnome-tweak" that will set font sizes and "dconf" doesn't appear to work.
I find it a bit amazing that an Alpha is released without a tool to adjust font size. Such a fundamental and essential thing. However...
Cheers, Mike

An alpha in Ubuntu really means "stable development snapshot." It isn't the same kind of alpha release you can expect from Firefox, for example, where most of the features are complete.

At any rate, this is all Gnome Control Centre 3. If you're interested in this changing, please take a look over there.

---

### Post by mc4man on 2011-06-12
> **mdurham said:**
> Thanks for the advice but, I can't find anything in "gnome-tweak" that will set font sizes and "dconf" doesn't appear to work.

The 'tweak tool' may be your best bet atm, don't see too much here in g-c-c (system settings

---

