---
title: "Switching from Qt3 to Qt4"
date: 2005-12-22
forum: Programming Talk
---

### Post by Jessehk on 2005-12-22
I currently am learning to program in Qt3, but I would like to switch to Qt4. The problem is that (what I suspect) Qt4 is not in my path. How would I go about switching all the tools (like qmake) to the qt4 installation (as well as updating the qt-assistant)? 

Thanks greatly in advance :)

---

### Post by asimon on 2005-12-23
The different designers are called designer-qt3 and designer-qt4. designer is a link (actually a link to a link) to one of those, per default designer-qt3. The same is true for assistant, moc, etc. So you can either call the qt4 versions directly or change the defaults where the links point to.

One way to do this is to use update-alternatives. This will change the default system wide, i.e. for all users.
```

sudo update-alternatives --config designer
```
will ask you what the default should be, so just choose the qt4 version. Do the same for assistant, qmake, etc.

To change it just for a single user you could put links into your ~/bin directory, i.e.
```

cd ~/bin
ln -s /usr/bin/moc-qt4 moc
```
The ~/bin path comes usually first in $PATH, and is thus searched first.

---

### Post by Jessehk on 2005-12-23
Thanks :)

After a lot of tinkering, I figured out exactly what you told me by myself. Thanks for your help regardless.

---

