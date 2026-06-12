---
title: "Error Installing Eclipse"
date: 2010-05-01
forum: Programming Talk
---

### Post by Axilus on 2010-05-01
Hello there,

I just installed Eclipse form the ubuntu software center. I started it up and proceeded to download the C/C++ development tools however I get this error message right after it finishes.

```
An error occurred while installing the items
  session context was:(profile=PlatformProfile, phase=org.eclipse.equinox.internal.provisional.p2.engine.phases.Install, operand=null --> [R]org.eclipse.pde 3.4.100.v201002111343, action=org.eclipse.equinox.internal.p2.touchpoint.eclipse.actions.InstallBundleAction).
  The artifact file for osgi.bundle,org.eclipse.pde,3.4.100.v201002111343 was not found.

```

Any suggestions?

---

### Post by Axilus on 2010-05-01
After some more solution hunting I have found this bug report that seems to deal with the same problem.

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2221921.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2221921.html)

---

### Post by thirdgen88 on 2010-05-02
I had to go into Synaptic and install the eclipse-jdt and eclipse-pde packages... At that point, I was able to successfully complete installation of the C/C++ development packages from within Eclipse (i removed ~/.eclipse after those packages just to start from baseline). 

Now I've got an issue with the Help erroring out... Seems that a bug report has already been filed on this as well:

[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/549904](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/549904)

---

### Post by Axilus on 2010-05-02
I gave up on trying to get C/C++ working in eclipse. I highly reccomened Netbeans. It worked the first time I installed it from the Ubuntu repositories.

I am also coming from VS in windows and I must say that Netbeans is almost at a good enough level to compete with it.

I setup Netbeans so I could do SDL and OpenGl programming. I had a bit of difficulty on that part, but if you need help with that at anytime I can assist.

---

