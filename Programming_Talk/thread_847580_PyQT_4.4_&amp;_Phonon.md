---
title: "PyQT 4.4 &amp; Phonon"
date: 2008-07-02
forum: Programming Talk
---

### Post by erikf154 on 2008-07-02
Doesn't PyQT 4.4 come with Phonon support (I'm using KDE4.1 beta)? When I try to import the phonon module in my python script it says it doesn't exist...

---

### Post by john.ennew on 2008-07-20
I'm getting the same error (I think):

```

python fooey.py
Traceback (most recent call last):
  File "fooey.py", line 3, in <module>
    from PyQt4.phonon import Phonon
ImportError: No module named phonon

```

Looking at the Synaptec Package manager in Ubuntu, PyQt4 is version 4.3.3-2ubuntu4.1 and libqt4 is version 4.3.4-0ubuntu3. I think to get Phonon to work you need version 4.4 for both of these.  I guess I will have to wait for the ubuntu packages to catch up, unless anyone can provide instructions on how to upgrade quicker?

---

### Post by erikf154 on 2008-08-21
I've got python-qt4 4.4.3 installed from the repo, however the phonon module still doesn't exist? How come?

---

### Post by keeler1 on 2008-10-07
This is extremely annoying.  Ubuntu is way behind the curve with qt libraries.

I need the webkit libraries for a project I am working on.  So I had to steal them from the intrepid repos.  Now I was thinking about doing some things with phonon but it isnt supported either.  The only way to get phonon support is in the kde libraries.

However, I am not developing for kde I am developing for linux/mac/windows.  I was going to use phonon but it will not work in ubuntu.  At least without compiling from source.


Is there any way we could hurry along the the devs to get phonon supported for qt without kde.

---

