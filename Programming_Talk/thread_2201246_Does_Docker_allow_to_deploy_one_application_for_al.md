---
title: "Does Docker allow to deploy one application for all Linux distribution?"
date: 2014-01-23
forum: Programming Talk
---

### Post by erotavlas on 2014-01-23
Hi,

I'm looking for a way to share a binary among several (all) linux distributions avoiding the problem of shared library dependencies (a.k.a. dependency hell). I read about the project [http://www.docker.io/](http://www.docker.io/). It is a container that promises a lightweight isolation of the application. In you opinion, does it possible to compile one binary put it into docker and share among all linux distribution without dependencies and other problems? And if yes, how much is the slowdown in running?
Thank you very much

Best Regards

---

### Post by lykwydchykyn on 2014-01-23
Well, it would allow doing this on all linux distributions that support docker and have it installed (and, I assume, you'd need to have compiled for the same cpu type, e.g. i386/amd64/etc).  I don't know how to quantify the slowdown, I'm sure it's less than virtualization but more than native code.

Seems like an extreme solution to the problem though; can't you statically compile in the dependencies?

---

### Post by erotavlas on 2014-01-23
Yes it is a possible-extreme solution to my problem. I would like to compile a code in a binary that works in every (hopefully) linux distribution, but I cannot do that a due to the dependecy hell. This is my thread [http://ubuntuforums.org/showthread.php?t=2200790](http://ubuntuforums.org/showthread.php?t=2200790) related to this problem. For the moment I solved by compiling in my machine and linking into the target machines.
If you have any idea or suggestion, I will appreciate it. :)

---

### Post by lykwydchykyn on 2014-01-23
Maybe you can describe the wider context of what you're trying to do.  Are you trying to package a program for commercial sale?  What sort of program is it?

I mean, docker could be a solution in some cases, but I doubt it would fly to require docker for, say, a game or desktop application.  I'm not even sure if docker can do X11 stuff without some kind of VNC-like connection to the container.

Keep in mind that docker containers are isolated from the host much like virtual machines, so if this application needs to interact with files on the system that isn't going to do it.

Based on your included dependencies I'm guessing this is some kind of graphical application, but that's just a guess.

FWIW, I have very little experience doing static compiling, I mostly responded to your thread because I've had some limited experience with docker.

---

