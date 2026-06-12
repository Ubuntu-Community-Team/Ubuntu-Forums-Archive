---
title: "install.sh fails, blames pythons &amp; bins"
date: 2011-11-07
forum: New to Ubuntu
---

### Post by ktrout75 on 2011-11-07
I'm on  Ubuntu 11.1 trying to set up a GIS box with FWTools 2.0.6, the most current stable  release. My install fails after downloading the correct [FWTools package]("http://www.fwtools.maptools.org"),  un-tarring it to /usr/local/, and running the install.sh file.
 
 The whole error message is: "./install.sh: 33: bin/python: not found."
 
 An error message like this raises more questions than it answers for this  Ubuntu noob. How can I differentiate between: 
a dependency problem concerning my  current python version;
an issue with the dll called 'python' in the  /bin/ folder of the app;
a simple path mix-up;
or something else entirely?
 
 Of course I'd like to get the tools working but more importantly I need to  understand how to poke around for answers given what looks like an ambiguous error message. Is it just a matter of starting with the most likely culprit?
 
 thanks and thanks again,
 Rob
 
 oh, and here are the set-up instructions:
```

 % tar xzvf FWTools-linux-0.9.5.tar.gz
 %cd FWTools-linux-0.9.5
 % ./install.sh
```

---

### Post by satanselbow on 2011-11-07
Whilst 2.0.6 is the latest version it does date back to 2009. If you google the error message there are numerous posts on various forum with the exact same problem...

At a guess it broke in one of the bigger python updates and should maybe now be considered broken abandonware :(

---

