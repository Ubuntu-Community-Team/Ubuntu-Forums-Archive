---
title: "Howto customize your GDM mouse cursor"
date: 2006-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by frostie on 2006-10-26
I was having trouble matching up the cursor theme in my edgy user account with the one used at the gdm login. Whilst I was using one style, once I logged out, a totally different theme took over.

I have the Human theme selected for my icons in the theme manager and the solution that eventually worked for me was:

First unpack the cursor theme you want to use into:

/usr/share/icons/Human/cursors

Then edit this file (swap emacs for your flavour):

$ sudo emacs /usr/share/icons/default/index.theme

and replace the current text with:

[Icon Theme]
Name = Human
Comment = Default icon theme
Inherits = Human

Logout and they should match.

Ive not actually tried this with any other theme selections so maybe if you use, for instance, crystalsvg then you should adjust the above accordingly.

I hope this helps someone.

---

