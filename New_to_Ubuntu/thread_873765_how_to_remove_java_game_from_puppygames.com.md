---
title: "how to remove java game from puppygames.com"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by Jareth on 2008-07-29
Can anyone tell me the proper way of doing this?

I stumbled on their site and tried one of their games, droid assault.
Its a pretty good game and I liked how well it runs on my system and it was easy enough to download and install.

I want to know how to remove it now.

It downloaded and installed from a 'droidassault.jnlp'  file which went through a load of java stuff. It has left an icon on my desktop too. I did think of just removing the desktop icon but I wasn't sure if their would be other bits of it that would need removing.

When I look at the properties for the desktop icon it says type:desktop configuration file

Can anyone help with this?

Ta!

EDIT: it should be puppygames.net, doh!

---

### Post by Voynix on 2008-07-29
You can go to System > Preferences > Sun Java 6 Control Panel. On the "General" tab, under the "Temporary Internet Files", click on "View", and then remove the game.

Since it is a jnlp downloaded file the game is only saved in a sandbox (.java/deployment/cache/6.0/). You can remove the desktop shortcut and all the files in your java cache directory without problems.

Cheers

---

### Post by Jareth on 2008-07-29
Thanks very much, that sounds great!

---

### Post by leyouki on 2009-08-24
hello!

I tried droid assault and want now to uninstall the game. I had a look in my home directory and there is a /droid assault directory with 24.3 Mio inside...

I deleted it and followed you instructions but it is just awful how this game can not be uninstalled correctly!

---

