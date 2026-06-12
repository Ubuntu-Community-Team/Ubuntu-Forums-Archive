---
title: "GNUstep Makefile and build environment - build fails"
date: 2010-04-12
forum: Programming Talk
---

### Post by macdudeosx on 2010-04-12
I successfully built and ran GNUstep Project Center and Gorm. I am porting a few of my applications I wrote on my mac to linux, but I can get it to build!

Every time I build, whether it is in the Terminal or in Project Center I get:
/common.make: No such file or directory
/aggregate.make No such file or directory
/application.make No such file or directory
make: ***No rule to make target '/application.make'. Stop.
==Build terminated!==

I looked in the Makefile Project Center generates and I figured the build environment is not working for Make because the lines that fail are:
include $(GNUSTEP_MAKEFILES)/common.make
include $(GNUSTEP_MAKEFILES)/aggregate.make
include $(GNUSTEP_MAKEFILES)/application.make

I edited my bash.bashrc file to include /usr/share/GNUstep/Makefiles/GNUstep.sh so that the specific variables like GNUSTEP_MAKEFILES point to  /usr/share/GNUstep/Makefiles I know this because when I open terminal and type echo $GNUSTEP_MAKEFILES I get  /usr/share/GNUstep/Makefiles

But for some reason, Make is not recognizing the environment variables, it just ignores them and points to the mount point for the make files, which is not where they are located. 

I could go through the Make file and manually put in the path for every variable, but that is definitely not the way I want to go.

Any thoughts anyone?

---

### Post by _lowell on 2010-04-20
*> > I could go through the Make file and manually put in the path for every variable, but that is definitely not the way I want to go.*

Not to mention that ProjectCenter will overwrite anything you enter in the Makefile with the default values.

Anyways, just a heads up - I ran into a similar issue a little bit ago (like half an hour ago) and found this post. I'm actually doing the exact same thing you are with the porting. But yeah; in case you haven't solved it - running make from the project folder will build the project perfectly, as long as the GNUSTEP_MAKEFILES env var is set.

---

### Post by howesda on 2011-07-08
I know this is an old post and this might be a bit late, but I fixed this by putting the call to /usr/share/GNUstep/Makefiles/GNUstep.sh in .gnomerc

Dave

---

### Post by slavik on 2011-07-08
back to the grave with you

---

