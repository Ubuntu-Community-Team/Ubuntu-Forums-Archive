---
title: "gedit plugin development in C"
date: 2010-10-25
forum: Programming Talk
---

### Post by Aboelnour on 2010-10-25
I'm Interesting to write gedit-plugins in C I've checked that [http://live.gnome.org/Gedit/NewMDIPluginHowTo](http://live.gnome.org/Gedit/NewMDIPluginHowTo) but i find it not good to start.

How can I get another informations about writing gedit plugins in C?
any help will be appreciated
Thanks in advance.

---

### Post by spjackson on 2010-10-25
Where are you starting from? What experience do you have with C?

If I was going to do this, I'd get the source for gedit, install any prerequisites and build gedit. Once I'd got that far, I would run generate-plugin.py which is mentioned at the end of that page. I'd build the sample and make sure I could run it. Then I'd tinker with it. Then I'd probably go and look at some of the many existing plugins that are available and see if I could find one similar to what I was trying to do. For finding alternative documentation, I'd use Google.

Which parts are you having a problem with?

---

