---
title: "How to get GRUB Menu for Recovery Mode?"
date: 2011-08-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by [Neurotic] on 2011-08-24
Hey all,

Started up my Oneiric test machine today, and it's just frozen at the login screen. Yay fun. Can't even ctrl+alt+1 to get a TTY screen either.

Normally, this is where I would boot up into a recovery mode from Grub, hop into root console, and try apt-get updating to see if any of my packages are broken (or at least have a look at dmesg).

The only thing is - when I boot up - there is no GRUB boot menu. How can I get it back? Can't seem to find a post on how to do this yet.

Thanks in advance!

---

### Post by dave01945 on 2011-08-24
i believe you press esc at start up just keep pressing until you see grub if not try holding shift

---

### Post by [Neurotic] on 2011-08-24
Found it.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Hit SHIFT for the menu.

Thanks anyway!

---

### Post by cariboo on 2011-08-24
You only run into grub not showing, when you only have one installation on your hard drive, I really recommend that during a testing phase, that you have at least one stable installation, just in case. Barring that at least do daily backups, if what you do on your computer is important to you.

I personally do two backups a day of my home directory, and restore to a stable install a couple of times a week. You never know when something is going to jump up and bite you. :)

---

