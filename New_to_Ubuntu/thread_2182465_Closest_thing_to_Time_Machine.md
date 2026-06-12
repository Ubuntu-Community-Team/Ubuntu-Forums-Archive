---
title: "Closest thing to Time Machine"
date: 2013-10-21
forum: New to Ubuntu
---

### Post by Danny_Michel on 2013-10-21
What I want is something that I can use to make incremental backups all day so that if anything goes wrong, I can reinstall Ubuntu then reinstall whatever the app is and do 'Full Restore' and all my apps, settings, everything is basically cloned. Is this even possible? And is this what I'm looking for? [http://peterpetrakis.blogspot.com/2013/06/automating-and-encrypting-duplicity.html](http://peterpetrakis.blogspot.com/2013/06/automating-and-encrypting-duplicity.html)

---

### Post by newb85 on 2013-10-21
I'm assuming you're looking for a GUI app.

Deja Dup is a great tool for incremental backups.  It's only intended for backing up your /home directory, so you'll need some other way of backing up what packages you have installed.  Fortunately, the Software Center has such a feature built in.  If you click File>Sync between computers, you can set up a USC account that will track what packages you have installed on your machine.

---

