---
title: "need installtion help with a program"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by futureal2032 on 2008-05-22
Hi all..

i am using Ubuntu 7.04.

i downloaded gyachi_1.1.26_lenny.sid_i386.deb from sourceforge.
as some of you may already be using it. Gyachi is a yahoo messenger client with webcam and voice support.

**when i tried to install.** (i double clicked the .deb file)  the installer gave me an error.
**"error: dependency not satisfiable - libasound2"**

so i downloaded libasound2 library .deb from packages.ubuntu.com servers.

when i** tried to install the libasound2 **library
it gives error
**"error: dependency not satisfiable - libc6"**

well..then i downloaded some libc6 files
and when i try to install the installer tells me Older version already available.
and the installer completes. 
b**ut i have not been able to install libasound2 and so no gyachi either.**

can anybody help me?

---

### Post by HotShotDJ on 2008-05-22
> **futureal2032 said:**
> so i downloaded libasound2 library .deb from packages.ubuntu.com servers...

...but i have not been able to install libasound2 and so no gyachi either
Have you checked System --> Administration --> Synaptic Package Manager for those dependencies?  I'm actually surprised that gdebi didn't satisfy the dependencies for you.  Of course, I'm using a Hardy (8.04) system, but libasound2 is in the repositories and is installed on my system.  In any case, check there first.

---

### Post by futureal2032 on 2008-05-22
> **HotShotDJ said:**
> Have you checked System --> Administration --> Synaptic Package Manager for those dependencies?  I'm actually surprised that gdebi didn't satisfy the dependencies for you.  Of course, I'm using a Hardy (8.04) system, but libasound2 is in the repositories and is installed on my system.  In any case, check there first.

thanks,
i will try your suggestion and get back.

---

### Post by futureal2032 on 2008-05-22
> **HotShotDJ said:**
> Have you checked System --> Administration --> Synaptic Package Manager for those dependencies?  I'm actually surprised that gdebi didn't satisfy the dependencies for you.  Of course, I'm using a Hardy (8.04) system, but libasound2 is in the repositories and is installed on my system.  In any case, check there first.

Hey i tried that
but i get the same error when i try to install Gyachi
all libraries starting from libc6 and libasound2 are now installed but i keep getting same errors.

---

### Post by HotShotDJ on 2008-05-22
> **futureal2032 said:**
> Hey i tried that
but i get the same error when i try to install Gyachi
all libraries starting from libc6 and libasound2 are now installed but i keep getting same errors.OK... that package is probably not compatible with your system.  You could try downloading the tarball and compiling it yourself (but using CheckInstall rather than the standard install).

I was going to suggest that upgrading to Hardy might solve your problem, but I just tested gyachi_1.1.26_lenny.sid_i386.deb on my system and get the very same error.

---

### Post by HotShotDJ on 2008-05-22
I found a gyachi package that will install on Hardy: [http://www.mediafire.com/?nlrmdlub4tv](http://www.mediafire.com/?nlrmdlub4tv)

I attempted to compile the sources, but it was a no-go, although my research on this problem concluded that the CVS version may sort out that problem.  I did not test it, though.

Thats about all I have for you.  I hope it was helpful.

---

