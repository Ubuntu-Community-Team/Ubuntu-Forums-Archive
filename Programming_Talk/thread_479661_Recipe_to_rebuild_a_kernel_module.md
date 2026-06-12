---
title: "Recipe to rebuild a kernel module?"
date: 2007-06-20
forum: Programming Talk
---

### Post by wkulecz on 2007-06-20
I need to modify and rebuild the bttv module from Ubuntu 6.06.  I've downloaded the kernel source and found the appropriate files but don't know how to actually build the module.

The Makefile in the /usr/src/linux-source/drivers/media/video gives "no targets" when I type make.

How to proceed?  My goal is simply to rebuild the bttv.ko module and use rmmod and insmod to test my changes.

TIA,
--wally.

---

### Post by 5-HT on 2007-06-20
Hi, you'll need to edit the makefile to build an individual module.
[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html)

cheers,

---

### Post by wkulecz on 2007-06-21
> **5-HT said:**
> Hi, you'll need to edit the makefile to build an individual module.
[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html](http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html)

cheers,

I have no clue as to what to edit the makefile to be.  It's not a standard Makefile but something to be used as part of the kbuild system.


I found this:  [http://glasnost.beeznest.org/articles/340](http://glasnost.beeznest.org/articles/340)  eventually after a Google search using some terms suggested by a thread I found in the "Packaging and Compiling Programs" sub-forum".  So I copied the /usr/src/linux-source/drivers/media/video directory to my home directory and followed its instructions.

This compiles the bttv.o moudule but the build dies on compiling video-buf-dvb.c and thus fails to create my bttv.ko module.  It also builds a bunch of stuff I don't care about or need to change.  

I'm currently commenting out lines in the Makefile that seem related to the failing dvb builds but things cascade, now cx88.c is failing, if this is not part of bttv.ko I can ignore it but there is damn little info as to how the many files in the directory play together and the error seems to stop the build process before bttv.ko is built.

--wally.

Edit:  Eventually I commented out enough stuff from the Makefile to let the build complete to make the bttv.ko module.  Now I'm off to rmmod bttv (the stock module) and then insmod the one I built which should be the same code at this point.  If this works I can proceed with my mods.  Presumably, the stuff I don't need that gets built will not change and hopefully not slow me down by being rebuilt for every change I do.

---

### Post by wkulecz on 2007-06-21
rmmod bttv failed because it was in use by bt878.  Easy enough to rmmod bt878 and then rmmod bttv.  But....  bt878.ko did not get built along with my bttv.ko module.

Stumped again.

But the good news is insmod /myhome/video/bttv.ko followed by modprobe bt878 gives me working video.  So unless modprobe silently removed my bttv version prior to reinstalling the stock version, my bttb.ko build seems sucessful.  Now to try and figure out why bt878.ko doesn't exist :(

--wally.

---

### Post by wkulecz on 2007-06-21
Apparently the bt878 module is loaded by the boot code, but not needed by my use of /dev/video0 and /dev/video1.  

The bt878 module appears to be part of the dvb stuff.  Trying to compile it by copying over the entire media directory (like I did for media/videoand running make ~/media leads to a ton of errors from include files including other include files but not knowing the correct path to find them.  They are all there in the media sub-tree somewhere.

At least I can apparently rebuild a working bttv.ko module now.  

--wally.

---

