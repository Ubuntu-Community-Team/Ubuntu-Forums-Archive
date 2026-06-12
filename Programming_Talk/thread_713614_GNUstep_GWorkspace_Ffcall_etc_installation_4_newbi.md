---
title: "GNUstep GWorkspace Ffcall etc installation 4 newbie"
date: 2008-03-02
forum: Programming Talk
---

### Post by quique123 on 2008-03-02
im newbie to linux.  I recently installed ubuntu on my dell laptop and the whole reason being to program on objectiveC.  So i proceeded to download GNUstep, Gworkspace, Gorm, and ffcall which i think are the basics for a windows like GUI development enviroment for objectiveC, kinda like MS Vistual Studio development for C++/C.

So i realized there is a GNUstep initialization script that installs GNUstep autmatically, without having to compile and install the make library and core library and the other 2 main libraries.  SO i dl that and  all other onto my ubuntu desktop.  dl the packages suggested before installing gnustep.  installed them using synaptic package manager.  then i went to terminal, gnu192 folder on my desktop and ran ./configure, then make then make install.  it all ran fine, ran ffcall and it ran fine once i moved the ffcall folder into the GNUstep directory installed on my user folder.  then i try to run ./configure in the gw folder but i get the error saying i must first run the gnustep initialization script first.

1.  if the gnustep initializations script runs fine, why is gworkspace ./configure file asking me to run it?!?!?!

mars

---

### Post by Can+~ on 2008-03-02
According to the gnustep faq, the only thing you should do is:

```
sudo apt-get install gnustep gnustep-devel
```

and it would automagically set everything. [http://wiki.gnustep.org/index.php/Platform:Linux](http://wiki.gnustep.org/index.php/Platform:Linux)

You did that and it's failing now? Or you tried to do it from a source file?

---

### Post by quique123 on 2008-03-03
At this address:

[http://gnustep.made-it.com/BuildGuide/](http://gnustep.made-it.com/BuildGuide/)

You will find in Chapter 4 section the following:

GNUstep can be build in various ways. The easiest is to use the GNUstep-Startup script, which can be found at [http://ftp.gnustep.org/pub/gnustep/core/](http://ftp.gnustep.org/pub/gnustep/core/).

I downloaded the file at the bottom which is version 1.9.2.  And at that directory on my desktop, via the terminal, i ran:

./configure, then make and then make install which is what ive read somewhere online i think at GNUstep.

This installed my GNUstep in my home directory, i know cause i saw that directory called GNUstep.  But then i read i had to install:

ffcall
gworkspace in ordr to have a gui environment
gorm
project center

But when i try to install ffcall or gworkspace, i get an error saying I have to run the GNUstep initilization script first.  

I just ran your script, it installed GNUstep supposedly, with a different introduction at the terminal.  im running ffcall and then ill run gworkspace to see what happens.  Is there a surefire way to see that ive successfully installed GNUstep?

I still get the same error when trying to run ./configure at the gworkspace folder.

---

