---
title: "Support multiple versions of Ubuntu in PPA"
date: 2010-09-02
forum: Packaging and Compiling Programs
---

### Post by rubenverweij on 2010-09-02
Hi all!

I was wondering how I could get my PPA to build a package for both Lucid and Maverick of the same version of the same package. (Are you still with me? ;)) Now, only maverick is supported because that's what was in the changelog. I changed it to lucid to upload it again but this was rejected, obviously. Can someone help me with this please? I couldn't find a solution either in this forum or in the packaging guide, nor in the launchpad ppa guide...
Thanks in advance!

---

### Post by southindian on 2010-09-03
These are the web services to the clients.

---

### Post by rubenverweij on 2010-09-03
Sorry - what do you mean exactly by that?

---

### Post by SevenMachines on 2010-09-03
As far as i remember, launchpad doesnt allow building say, a maverick package and a lucid package in the same ppa. I think the options are (although i' happy to be corrected on this :) ). Either

* On the ppa page theres an option to copy package. You can then copy the build package from maverick to lucid within the same ppa. If you try to use the rebuild option here and the target is the same ppa itll fail. 

* Have a separate ppa for distributions. i have 'release' (lucid) and 'release+1' (maverick). You can then copy *and* rebuild the package for a different distribution

There may be new ways to do this with the new 'build recipes' feature but i havent looked at that much yet

---

### Post by SevenMachines on 2010-09-03
Indeed, if you set up a build recipe on your package then you can select any number of distributions to build for. Build recipes are cool :)  must remember to try and get mine to work sometime!
[https://help.launchpad.net/Packaging/SourceBuilds/GettingStarted](https://help.launchpad.net/Packaging/SourceBuilds/GettingStarted)

---

