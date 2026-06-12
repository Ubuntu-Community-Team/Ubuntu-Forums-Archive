---
title: "Change keyboard map from Ubuntu as MacBook"
date: 2022-08-05
forum: New to Ubuntu
---

### Post by trifek on 2022-08-05
I on my live use MacBook. Now et work I must use laptop with Ubuntu 22.04LTS, Gnome 42.2, X11(Dell).
Is posible set keyboard map as Mac on Ubuntu?




For example I mean shortcuts, e.g. command + z, command + a etc.


I can use remote Apple keyboard if its needed :)

---

### Post by ActionParsnip on 2022-08-07
Do you mean you want to use a mac keyboard with Ubuntu? Is this the requirement here, please?

---

### Post by trifek on 2022-08-08
I'd like to use macbook keyboard shortcuts on ubuntu. E.g. command + z, command + a etc. :) I have dell

---

### Post by ActionParsnip on 2022-08-08
Command + Z seems to be the shortcut for undo. CTRL + Z does this in Ubuntu and Windows.
Command + A does select all. CTRL + A does this in Windows and Ubuntu as well.... Am I missing something here?

---

### Post by trifek on 2022-08-09
it's all true what you write. I need to change to CTRL + Z to Ubuntu Command + Z, CTRL + A to Command + A etc

---

### Post by Impavidus on 2022-08-09
There are some guidelines and some applications outsource such key combos to the same library, so they are automatically the same, but in general, such key combos are defined per application. Instead of changing this setting in every application (which may be hardcoded), you may want to change the command key so that it acts as a ctrl key.

This is a bit older, but it may still work:
[https://askubuntu.com/questions/521202/make-the-ctrl-and-super-cmd-keys-behave-like-on-os-x](https://askubuntu.com/questions/521202/make-the-ctrl-and-super-cmd-keys-behave-like-on-os-x)
[https://askubuntu.com/questions/545752/how-to-achieve-mac-like-use-of-ctrl-and-cmd-keys-on-apple-keyboard](https://askubuntu.com/questions/545752/how-to-achieve-mac-like-use-of-ctrl-and-cmd-keys-on-apple-keyboard)

You can use the xev tool to find the keycode associated with a particular key.

---

