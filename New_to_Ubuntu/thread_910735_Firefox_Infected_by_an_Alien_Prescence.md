---
title: "Firefox Infected by an Alien Prescence"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by E.T.Smith on 2008-09-04
The "kcontrol" application was recently pointed out to me as the simplest way to install fonts, and it seems have worked fine for that purpose. Except now I have a rather bizarre problem. After the install of a few dozen fonts in one go, Firefox has randomly chosen to make one the default for rendering text on most web pages. Specifically, I'm now squinting to make out the spidery text of:
[IMG]http://www.acidfonts.com/graphics/alienleague.gif[/IMG]
A title font which when rendered down to standard page viewing scale is nigh illegible.

I have no idea why this happened. I never opened any option for altering default font selections, most definitely not in firefox. The Gnome font preference box, the one in kcontrol (which includes a sub-menu for fonts in internet applications) and the one in firefox are still set to the defaults. What am I missing?

---

### Post by steveneddy on 2008-09-04
In Firefox

Edit --> Preferences --> Content

Middle of the box there is a selection area for the default font to use in Firefox.

---

### Post by E.T.Smith on 2008-09-05
> **steveneddy said:**
> In Firefox

Edit --> Preferences --> Content

Middle of the box there is a selection area for the default font to use in Firefox.
As I said in the first post, I have already checked that font setting, and it is clearly set to the default and not "Alien League", so the problem is coming from somewhere else. Further, no matter what I change that font setting to, the display remains stuck on "Alien League".

EDIT: Actually, some of the text does change. The title "Quick Reply" and similar can shift, but the text in this reply remains as "Alien League".

---

### Post by E.T.Smith on 2008-09-05
I've taken the blunt sledgehammer approach by just deleting the "Alien League" font from my system, which has restored the text in firefox to a legible state. I still have no idea why the shift occured; as far as I saw, no other applications were affected.

I suspect using kcontrol for font installation was the ultimate cause. Wherever it installed them, it wasn't in the usr/share/font folder, and I suspect kcontrol's method is not fully compatible with gnome's organization.

---

### Post by Flimm on 2008-09-05
So can you mark this thread as solved, or do you still have unanswered questions?

---

### Post by E.T.Smith on 2008-09-05
> **Flimm said:**
> So can you mark this thread as solved, or do you still have unanswered questions?
Unsolved, since the mechanics behind the problem are still unknown, or how to prevent it from repeating when I next install fonts.

---

### Post by steveneddy on 2008-09-06
This sounds like a silly question, but are you using Ubuntu or Kubuntu?

Gnome or KDE?

kcontrol is a KDE application and if you are using Gnome, you may run into issues.

HINT:

in your /home folder, add a folder named
[B]
.fonts[/B]

notice the dot before the file name. This makes it a hidden folder.

To view hidden folders, open the /home folder and hit the ctrl+h keys.

Scroll down as they are after the regular folders.

Put your new fonts in the **.fonts** folder.

After you install new fonts, run this code.

```
fc-cache -fv
```

Sometimes we need to restart for some reason, but this should get you going.

---

