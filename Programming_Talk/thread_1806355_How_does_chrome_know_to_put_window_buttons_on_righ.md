---
title: "How does chrome know to put window buttons on right or left"
date: 2011-07-17
forum: Programming Talk
---

### Post by bonfire89 on 2011-07-17
Hi there, I hope the at I am on the the right board here...

I am trying to make the chromium window buttons go on the left in xfce. I'm assuming that in gnome chromium references some sort of theme file to check which side the buttons should be on. Perhaps in xfce I can artificially create this file?

=/

Let me know.

Thanks

---

### Post by Bodsda on 2011-07-18
> **bonfire89 said:**
> Hi there, I hope the at I am on the the right board here...

I am trying to make the chromium window buttons go on the left in xfce. I'm assuming that in gnome chromium references some sort of theme file to check which side the buttons should be on. Perhaps in xfce I can artificially create this file?

=/

Let me know.

Thanks

Hi,

I have no idea how XFCE does it, but for gnome it is set via the 'button_layout' key:value in gconf-editor > apps > metacity > general

HTH,
Bodsda

---

