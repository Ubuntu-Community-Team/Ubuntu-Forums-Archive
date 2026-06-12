---
title: "Mono SendKeys"
date: 2010-08-02
forum: Programming Talk
---

### Post by drehb on 2010-08-02
Hi, I've got a cross platform application built with Mono ([http://code.google.com/p/android-pcbcr/](http://code.google.com/p/android-pcbcr/)).  I was using a project called InputSimulator to simulate keystrokes in Windows, and xvkbd to do the same in Linux.  I came across the System.Windows.Forms.SendKeys class and wanted to move to using that for greater portability and simplicity.  The change is working in Windows, but it seems that SendKeys.Send() doesn't work in Ubuntu though...anybody else ran into this problem or have any idea how to get it working?  I've got Ubuntu 10.04 and tried the Mono runtime version in the repositories(2.4.4?), as well as v2.6.3 from [http://badgerports.org/](http://badgerports.org/).

---

