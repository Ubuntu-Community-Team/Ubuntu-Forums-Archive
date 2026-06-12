---
title: "cant install PyOgre"
date: 2007-01-30
forum: Programming Talk
---

### Post by Choad on 2007-01-30
i downloaded pyogre through svn, as it said i should do on the pyogre site. then i tried to install it
```

richard@richard-laptop:~$ cd dev-1.2.0/
richard@richard-laptop:~/dev-1.2.0$ sudo python setup.py install
running install
running build
running build_ext
building 'pyogre._ogre' extension
swigging pyogre/ogre/ogre.i to pyogre/ogre/ogre_wrap.cxx
swig -python -c++ -modern -Ipyogre/ogre -I/usr/include/OGRE -o pyogre/ogre/ogre_wrap.cxx -outdir pyogre pyogre/ogre/ogre.i
pyogre/ogre/OgrePose.i:13: Error: Unable to find 'OgrePose.h'
pyogre/ogre/OgreAnimable.i:16: Error: Unable to find 'OgreAnimable.h'
pyogre/ogre/OgreRenderQueueInvocation.i:25: Error: Unable to find 'OgreRenderQueueInvocation.h'
pyogre/ogre/OgreManualObject.i:14: Error: Unable to find 'OgreManualObject.h'
pyogre/ogre/OgreBillboardChain.i:123: Error: Unable to find 'OgreBillboardChain.h'
pyogre/ogre/OgreRibbonTrail.i:13: Error: Unable to find 'OgreRibbonTrail.h'
error: command 'swig' failed with exit status 1
richard@richard-laptop:~/dev-1.2.0$ 
```

now if i manually find each of those files on the internet, it gets a little further but complains a LOT and then fails again.

how can i install pyogre? any help? i really want to start learning ogre/python

---

### Post by meng on 2007-01-30
Sounds like you need to have both python and ogre installed in order to use this program of yours. Only python is installed by default with Ubuntu (AFAIK). So try installing ogre (universe repositories). My best guess would be:
sudo apt-get install libogre-dev

then try compiling pyogre again.

---

### Post by Choad on 2007-01-30
done and done. installed them ages ago :)

[img]http://img246.imageshack.us/img246/808/screenshot2xm8.png[/img]

---

### Post by kripkenstein on 2007-01-30
Look for those files (that it says it can't find), are they somewhere on your hard drive?

---

### Post by Choad on 2007-01-30
> **kripkenstein said:**
> Look for those files (that it says it can't find), are they somewhere on your hard drive?
i've done this, put them in the right directory, and it got a lot further but it was spewing all kinds of ugly errors and then gave up a while later

they were not on my hard disk. i got them off the net

---

