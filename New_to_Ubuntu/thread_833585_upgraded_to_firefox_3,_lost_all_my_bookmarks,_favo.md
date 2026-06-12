---
title: "upgraded to firefox 3, lost all my bookmarks, favorites...."
date: 2008-06-18
forum: New to Ubuntu
---

### Post by ninja senses on 2008-06-18
heres what i ran in the terminal:

sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
sense@sense-ubuntu:~$ rm firefox-3.0.tar.bz2
sense@sense-ubuntu:~$ sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sense@sense-ubuntu:~$ sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sense@sense-ubuntu:~$ sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
Adding `local diversion of /usr/bin/firefox to /usr/bin/firefox.ubuntu'
sense@sense-ubuntu:~$ sudo ln -s /opt/firefox/firefox /usr/bin/firefox

 how can I get everything back?

---

### Post by ninja senses on 2008-06-18
super frustrated

---

### Post by y-lee on 2008-06-18
Sorry about your problem.

I don't use FF3 yet so I am not sure this will help but try from FF3's menu Bookmarks -> Organize Bookmarks -> Import and Backup -> Import HTML... -> from an HTML File and navigating to your back up copy of the mozilla folder and importing file "bookmarks.html", located in the Firefox2 profile folder.

You may also want to read [Lost Bookmarks]("http://kb.mozillazine.org/Lost_bookmarks")

If you also lost your passwords see [Transfer Your Firefox 2 Passwords into Firefox 3]("http://lifehacker.com/396431/transfer-your-firefox-2-passwords-into-firefox-3")

---

### Post by ninja senses on 2008-06-18
nevermind, my backup is overwritten

---

