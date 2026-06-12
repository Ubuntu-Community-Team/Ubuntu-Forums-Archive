---
title: "OGRE - plugin"
date: 2007-05-10
forum: Programming Talk
---

### Post by prolapsedisk on 2007-05-10
I'm missing the ogre plugin_cgprogrammanager.so library from the libogre deb file. I think this plugin is there only if you've got the nvidia cg toolkit. But is it supposed to be in the deb file in the first place? I'm trying to run an app that requires this, but i don't know where to get it.

Can someone help ?

---

### Post by heimo on 2007-05-11
I searched packages and couldn't find that file in repositories. Searching Google found  interesting chapter in the end of this guide:
[http://web.media.mit.edu/~phaeton/ogre/OgreUbuntuInstallNotes.html](http://web.media.mit.edu/~phaeton/ogre/OgreUbuntuInstallNotes.html)

> 
Anyway, what kept happening to me is that the 'make' process would create these libraries, but because of some silly error, would never actually copy them over before the cleanup phase of 'make' and 'make install' removed them. So what I had to do was interrupt my make process after it had built these libraries, grep for the necessary files (they will be in some strange *.soU format, and you will have to rename them when you move them to your /usr/local/lib/) and manually put them where the ogre executables were looking. Needless to say, this was extremely annoying, but in the end it all worked out.

---

