---
title: "Firefox ticking checkbox problem"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by PetePete on 2008-06-05
When ticking checkboxes and radiobuttons on websites in firefox you need to click around the box in order to check it. Clicking inside the checkbox does nothing.

any ideas?!

---

### Post by Dr Small on 2008-06-05
Never heard of that problem before. By the way, what version of Firefox are you using... Firefox 3 beta 5 ?

Dr Small

---

### Post by PetePete on 2008-06-05
yes it is firefox 3, beta 5. Standard issue hardy version.

---

### Post by jtsop on 2008-06-06
I have the same problem (3 pcs) with FF RC1. I've noticed that with Hardy for the first time.

---

### Post by PetePete on 2008-06-10
shameless bump...

anyone?!!

---

### Post by CopaceticOpus on 2008-06-24
I have this problem as well. I get the impression that clicking on the checkbox does activate it, but the graphic of the checked box can only be seen once focus is moved off the box (by clicking elsewhere.) This also occurs for radio buttons.

I've also noticed some ugliness with my tabs. The icons for many sites extend a pixel or two below the tab bar, onto the border beneath the tabs. Also, the active tab has a line below it which is wider than the tab and also a pixel too low. It just looks goofy.

This is merely cosmetic. It isn't having any real negative effects on my browsing. I thought it was just a FF3 thing until I installed on Windows and these issues didn't appear.

---

### Post by bertilow on 2008-06-24
> **CopaceticOpus said:**
> I have this problem as well. I get the impression that clicking on the checkbox does activate it, but the graphic of the checked box can only be seen once focus is moved off the box (by clicking elsewhere.) This also occurs for radio buttons.

I confirm this on Kubuntu Hardy, Firefox 3. It might be related to the KDE theme, but I haven't tested that.

---

### Post by gtdaqua on 2008-06-24
> **CopaceticOpus said:**
> I have this problem as well. I get the impression that clicking on the checkbox does activate it, but the graphic of the checked box can only be seen once focus is moved off the box (by clicking elsewhere.) This also occurs for radio buttons.

I've also noticed some ugliness with my tabs. The icons for many sites extend a pixel or two below the tab bar, onto the border beneath the tabs. Also, the active tab has a line below it which is wider than the tab and also a pixel too low. It just looks goofy.

This is merely cosmetic. It isn't having any real negative effects on my browsing. I thought it was just a FF3 thing until I installed on Windows and these issues didn't appear.

A bug has been filed [here]("https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/223055"). But apparently, no resolution yet because it is a bug in a different package - gtk-qt-engine.

Go [here]("https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/223055/comments/13") for a more specific comment on the bug.

---

### Post by bertilow on 2008-06-24
> **gtdaqua said:**
> A bug has been filed [here]("https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine/+bug/223055").

In that discussion someone wrote that choosing a specific GTK theme for GTK applications (not just using a KDE style) fixes the problem. I can confirm that. Problem solved for me.

System Settings -> Look & Feel -> Appearance -> GTK Styles and Fonts -> GTK Styles -> Use another Style -> (Pick one)

(Maybe you need to have parts of Gnome installed.)

---

### Post by gtdaqua on 2008-06-24
> **bertilow said:**
> In that discussion someone wrote that choosing a specific GTK theme for GTK applications (not just using a KDE style) fixes the problem. I can confirm that. Problem solved for me.

System Settings -> Look & Feel -> Appearance -> GTK Styles and Fonts -> GTK Styles -> Use another Style -> (Pick one)

(Maybe you need to have parts of Gnome installed.)

Its weird in my system. I use Kubuntu Hardy 32-bit and when I get there (System Settings -> Look & Feel -> Appearance -> GTK Styles and Fonts -> GTK Styles -> Use another Style) and select "qt" from the drop box and click apply. But the setting is not saved! I had to use "raleigh" and that stays.

But I am getting the classical Firefox interface as against to the latest glossy one. Does your glossy firefox interface stay even after the change?

---

### Post by Loevborg on 2009-07-08
I still have the same problem as the OP (on Kubuntu Hardy). Changing the style to Raleigh, rather than QT, resolves the problem. It's uglier, but at least you see if checkboxes are ticked or not. Rather odd that this bug should not be fixed by now in an LTS release.

---

