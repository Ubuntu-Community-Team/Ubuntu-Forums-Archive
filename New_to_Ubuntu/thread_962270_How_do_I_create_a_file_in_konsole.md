---
title: "How do I create a file in konsole?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by Matt86 on 2008-10-29
Very simple question, how do I create a file in Konsole?

I'm using Kubuntu 8.10 and in order to enable SHMConfig I need to create a policy file for HAL - as xorg.conf is no longer used in that manner.

I know what I need create, and what script to include, I just don't know how to create a file!

I'm aiming to create "/etc/hal/fdi/policy/11-synaptic-options.fdi"

Thanks!

---

### Post by macogw on 2008-10-29
Just start up a text editor.  For example:
gksu gedit /etc/hal/fdi/policy/11-synaptic-options.fdi

When you save it, it's created.

---

### Post by zakirs on 2008-10-29
if u just want to create a empty file u can use  "touch" command

---

### Post by macogw on 2008-10-29
doh, KDE user...dumb me

kdesu instead of gksu
and instead of gedit umm... it's either kate or kedit, whatever KDE's text editor is.

---

### Post by Matt86 on 2008-10-29
Thanks for your help, did the trick - I know it's a very basic question, but I'm still coming to terms with konsole!

Thanks again!

---

