---
title: "Cryptkeeper in 14.04"
date: 2014-05-15
forum: New to Ubuntu
---

### Post by keiths2 on 2014-05-15
Has anyone installed Cryptkeeper and seen it working in 14.04?
I installed it, the icon sits in my Launcher, when I click on it it, it sort of throbs for a couple of seconds, then nothing.
What's supposed to happen? Say I have a text file open on my desktop and want to save it into an encrypted(?) folder somewhere/anywhere I can find it. In very simple terms, how do I do this?
TIA

---

### Post by mcduck on 2014-05-15
Cryptkeeper still tries to use the old notification icon system instead of indicator applets, which isn't supported any more and therefore you can't see or access Cryptkeeper even when it's running.

It probably is possible to still manually whitelist it's icon to make it appear, but I'd really just recommend swithing to better supported [Gnome Encfs Manager]("http://www.webupd8.org/2013/05/gnome-encfs-manager-cryptkeeper.html").

---

### Post by keiths2 on 2014-05-15
Thanks for the info, my head was hurting :)

---

