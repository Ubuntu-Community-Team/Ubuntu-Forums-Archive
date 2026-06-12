---
title: "Setting up Cross Compile Environment"
date: 2008-06-30
forum: Programming Talk
---

### Post by Elsven on 2008-06-30
Hello,

    I am trying to set up a development environment, I have the cross compiler I  need for my arm board however I am not sure where to put my path variables, I am using an Eclipse environment for development so any help would be appreciated.  The things I want to export are:

```
export PATH=/opt/br/bin:$PATH

export ARCH=arm
export CROSS_COMPILE=arm-linux-uclibc-
export CROSS=arm-linux-uclibc-

#export PATH=/opt/br/bin:/home/gprice/bin:/usr/local/bin:/usr/bin:/usr/X11R6/bin:/bin:/usr/games:/opt/gnome/bin:/opt/kde3/bin:/usr/lib/jvm/jre/bin:/usr/lib/mit/bin:/usr/lib/mit/sbin:/usr/lib/qt3/bin

```

Regards,

Richard

---

### Post by Elsven on 2008-06-30
I am surprised to see no response yet.  Assuming this is the right place for this post let me know if you need more information on the problems so I can resolve it and if this is the wrong place for this sort of question let me know where would be best for me to find what I need.  

Regards,

Richard

---

### Post by BoneKracker on 2008-07-12
Look for project-specific or toolchain-specific or build-configuration settings within Eclipse itself.

While you could export these variables just about anywhere as system variables within GNU/Linux (e.g., from your ~/.profile file), you probably don't want them to be universally applicable.  Most build systems, including those managed by IDEs such as Eclipse, profile facilities for temporarily setting such variables within a limited scope (such as automatically placing them within a dynamically-generated makefile or such).

You might try the eclipse wiki to get more accurate, detailed advice.

---

### Post by pocketchange on 2009-03-04
I'm trying to get something similar.  I usually use emacs, but I'm not too particular about which IDE I'm using as long as I have a good set of tools to cross compile for arm.  Did you have any success finding a solution for this?

Shane

---

