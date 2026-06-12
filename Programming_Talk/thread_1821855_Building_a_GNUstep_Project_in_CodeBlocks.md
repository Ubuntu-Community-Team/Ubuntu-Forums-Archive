---
title: "Building a GNUstep Project in Code::Blocks"
date: 2011-08-09
forum: Programming Talk
---

### Post by lightstream on 2011-08-09
I'm having trouble building the oolite space trading game from within Code::Blocks and could do with some help.

The problem seems to be to do with GNUstep - oolite was originally written for Apple using Cocoa, so on Linux you need to use GNUstep.

I can compile from the command line fine, as long as I execute the GNUstep script (/usr/share/GNUstep/Makefiles/GNUstep.sh) first in order to set up various environment variables.

So I've added this script as a 'Prebuild Task' in Code::Blocks, and I can see from the Build Log that it is running correctly.

However I get the error "CoreFoundation/CoreFoundation.h: No such file or directory" w.r.t. code in a folder called 'Mac-specific', which indicates the GNUstep stuff isn't working properly and the project is being compiled as if it was on Apple.

---

### Post by schauerlich on 2011-08-10
Is there a particular reason you're doing it this way? I seems from the site that it has a native linux version.

[http://www.oolite.org/download.shtml](http://www.oolite.org/download.shtml)

---

### Post by lightstream on 2011-08-11
Mainly I just want to mess about with the code.

My understanding is that when you download the source, it comes with the native Apple stuff and also stuff for GNUstep.

The GNUstep.sh script sets up environment vars which are then used during compilation to determine whether to use the GNUstep stuff (ie you're on linux) or the Cocoa stuff (ie you're on Apple).

It works OK on the command line, but not when I try to build from Code::Blocks. 

All I can think is that maybe it's because environment vars that are set up by a pre-build step are no longer available during compilation?

---

