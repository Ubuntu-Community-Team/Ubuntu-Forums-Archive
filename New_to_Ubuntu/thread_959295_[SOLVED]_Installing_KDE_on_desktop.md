---
title: "[SOLVED] Installing KDE on desktop"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by HellNoire on 2008-10-26
Hey

Trying to install KDE onto my desktop, but only 3.5 because I don't like the look of 4.

Does it install 3.5 by default? Or is there a way to make 4 look like 3.5?

Thanks

---

### Post by SuperSonic4 on 2008-10-26
You can always get kubuntu hardy (the LTS means it will be supported) SUSE 10.3 or Mandriva 2008.1 (all old now though)

Are there any particular aspects of KDE4 that you don't like? I know there is a program that allows you to have two rows on the taskbar

---

### Post by HellNoire on 2008-10-26
All I want is the legit KDE, because right now, my GNOME is customised to look like KDE 3.5 and I just want the fact that it looks like the start menu and orgnised for the newbie. 

This is really for my parents because they can't understand how GNOME sets things up apparently, so that's what I'm worried about. The new aspect of the tabbed start menu messes them up, same with the widgets.

I think I'm just going to give them GNOME but skinned or something.

---

### Post by ibuclaw on 2008-10-26
In hardy, KDE 3.5 and KDE4.0 are both in separate packages in the repository.

The KDE3.5 metapackage is kde
The KDE4.0 metapackage is kde4

But, you probably only want the core packages if you plan to be using both gnome and KDE, so run this through a term
```
sudo apt-get install kde-core
```
Or search **kde-core** in synaptic and install

Regards
Iain

---

### Post by niccholaspage on 2008-10-26
I am running Intrepid and there is know sign of KDE 3 in it... You will want to keep Hardy Heron.

---

### Post by HellNoire on 2008-10-26
Thanks tinivole, that will help. Now I can help them install KDE. My dad and mom wanted something virusfree and easy to use, I showed them Linux and they loved it. So this is the next step, to make it even easier on them.

---

### Post by HellNoire on 2008-10-26
Consitering Heron's installed right now, I've got no problems with that, lol.

---

