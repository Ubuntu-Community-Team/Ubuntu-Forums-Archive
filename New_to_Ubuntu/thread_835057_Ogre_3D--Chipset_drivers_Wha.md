---
title: "Ogre 3D--Chipset drivers? Wha?"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by ceclauson on 2008-06-20
Hello!

I'm trying to install [Ogre 3D]("http://www.ogre3d.org") on my computer, and one of the problems was that the demos didn't work.  I [posted]("http://www.ogre3d.org/phpBB2/viewtopic.php?t=42276") about this on the Ogre forums, and a moderator, after examining the output of my run, thought that I needed to install the right chipset drivers so that my graphics card will do its thing.

My chipset is GM965 Express, and the graphics "card" is X3100, which is integrated into the chipset.  The page on Intel's website is  [here]("http://www.intel.com/products/chipsets/Gm965/index.htm").  After navigating it and looking for linux drivers, I came across some text that recommended that linux users should consult their distributors, and that linux driver software on the site was mainly for developers and maintainers.  And anyways, if I did download anything, be it a .tar file with binaries or source code, I wouldn't really know what to do with it.

So that's the situation.  I guess my question would be, how do I get the correct drivers for my chipset?  Anything that anyone can tell me to enlighten me would be appreciated.

Thanks,
Cooper

---

### Post by Dynaflow on 2008-06-20
That chipset has been the bane of my (and my Compaq's) existence for quite some time.  It's not exactly a top-flight graphics powerhouse to begin with, and until recently, Linux support for it wasn't simply bad -- it was crippled.  I have noticed it sucking markedly less since I upgraded to Hardy, but in the end, it's still cheap, commodity hardware from the shallow end of the graphics-acceleration pool.  

To top it all off, the Linux driver seems to have been an afterthought, so flawed that the Compiz Fusion people felt the need to [specifically blacklist it]("http://www.realistanew.com/2008/01/12/compiz-updates/").  Things are [slowly getting better]("http://www.phoronix.com/scan.php?page=news_item&px=NjM4OQ") on that front, though.

[To quote]("http://www.linuxquestions.org/questions/mandriva-30/intel-965-graphics-troubles-487330/") a senior member at another forum, when confronted with another member's difficulties with the Intel 965 chipset: "Three options. One, get a real graphics card. Two, turn off AIGLX when using a crappy intel and see if that at least gets you dri support. Three, install the open source driver intel now provides for free."  

You should have that driver installed by default in Hardy, I believe, in the xserver-xorg-video-intel package.

---

