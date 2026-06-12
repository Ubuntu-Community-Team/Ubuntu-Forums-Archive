---
title: "Psp programming: compiling error"
date: 2009-06-14
forum: Programming Talk
---

### Post by spylogo on 2009-06-14
I have spent many hours trying to figure this out, but I have no idea what to do.

Error= make: psp-config: Command not found
          Makefile:24: /lib/build.mak: No such file or directory
          make: *** No rule to make target `/lib/build.mak'.  Stop.
(I used the standard makefile for 3xx)

       When I type make into the terminal it works fine, and when I type in echo $PSPSDK I get the correct path, but the IDE won't work at all. I tried it on both Anjuta and KDE. I also added the three lines that you need to bashrc. Can someone please help?

---

### Post by Wra!th on 2009-06-15
> **spylogo said:**
> I have spent many hours trying to figure this out, but I have no idea what to do.

Error= make: psp-config: Command not found
          Makefile:24: /lib/build.mak: No such file or directory
          make: *** No rule to make target `/lib/build.mak'.  Stop.
(I used the standard makefile for 3xx)

       When I type make into the terminal it works fine, and when I type in echo $PSPSDK I get the correct path, but the IDE won't work at all. I tried it on both Anjuta and KDE. I also added the three lines that you need to bashrc. Can someone please help?
You need to add the executable path to your IDEs too probably... Not sure if they pick up on the PATH you define using bashrc or whatever you use to set your path. Check around your IDEs settings for a path variable.

---

### Post by spylogo on 2009-06-17
I did, but I must be an idiot, since I didn't find any for either of the IDE's I use. Not to mention that I don't have the screen resolution set up right, since I couldn't get it configured correctly.

---

