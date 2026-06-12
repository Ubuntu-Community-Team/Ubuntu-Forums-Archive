---
title: "Linux GUI programming using &quot;C&quot;"
date: 2009-06-20
forum: Programming Talk
---

### Post by valex on 2009-06-20
Hi.
I want to know about references about Linux GUI programming using "C". what am I follow?

---

### Post by Simian Man on 2009-06-20
Of the Linux GUI libraries, the only one that uses C as its base language is GTK.  I'd suggest [this tutorial]("http://library.gnome.org/devel/gtk-tutorial/stable/"), it seems to be perfect for you.

---

### Post by valex on 2009-06-21
thanks. it's helpful for me.

---

### Post by worksofcraft on 2010-02-21
sudo aptitude install gnome-core-devel build-essential

gives me a bunch of error messages ending in:

The following actions will resolve these dependencies:

Downgrade the following packages:
libcamel1.2-14 [2.26.1-0ubuntu2 (now) -> 2.26.1-0ubuntu1 (jaunty)]
libedataserver1.2-11 [2.26.1-0ubuntu2 (now) -> 2.26.1-0ubuntu1 (jaunty)]
libexpat1 [2.0.1-4ubuntu0.9.04.1 (now) -> 2.0.1-4 (jaunty)]
libfreetype6 [2.3.9-4ubuntu0.1 (now) -> 2.3.9-4build1 (jaunty)]
libglib2.0-0 [2.20.1-0ubuntu2.1 (now) -> 2.20.1-0ubuntu2 (jaunty)]
libglib2.0-data [2.20.1-0ubuntu2.1 (now) -> 2.20.1-0ubuntu2 (jaunty)]
libgnome-desktop-2-11 [1:2.26.1-0ubuntu2 (now) -> 1:2.26.1-0ubuntu1 (jaunty)]
libnautilus-extension1 [1:2.26.2-0ubuntu2 (now) -> 1:2.26.2-0ubuntu1 (jaunty)]
libnspr4-0d [4.7.5-0ubuntu0.9.04.1 (now) -> 4.7.3-0ubuntu2 (jaunty)]
libsoup-gnome2.4-1 [2.26.0-0ubuntu3 (now) -> 2.26.0-0ubuntu2 (jaunty)]
libsoup2.4-1 [2.26.0-0ubuntu3 (now) -> 2.26.0-0ubuntu2 (jaunty)]
libsqlite3-0 [3.6.10-1ubuntu0.2 (now) -> 3.6.10-1 (jaunty)]
libxcb-render0 [1.1.93-0ubuntu3.1 (now) -> 1.1.93-0ubuntu3 (jaunty)]
libxcb1 [1.1.93-0ubuntu3.1 (now) -> 1.1.93-0ubuntu3 (jaunty)]
libxi6 [2:1.2.0-1ubuntu1.1 (now) -> 2:1.2.0-1ubuntu1 (jaunty)]
libxklavier12 [3.9-0ubuntu2 (now) -> 3.9-0ubuntu1 (jaunty)]
libxml2 [2.6.32.dfsg-5ubuntu4.2 (now) -> 2.6.32.dfsg-5ubuntu4 (jaunty)]

Score is 570

Accept this solution? [Y/n/q/?]

So by "downgrading" I do wonder what will then stop working? Dis you have the same problem?

---

