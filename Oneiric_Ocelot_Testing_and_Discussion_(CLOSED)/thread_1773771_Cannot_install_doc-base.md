---
title: "Cannot install doc-base"
date: 2011-06-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by xxhopingtearsxx on 2011-06-02
I was upgrading to Ubuntu 11.10 Alpha and I got this error:

> Could not install 'doc-base'

The upgrade will continue but the 'doc-base' package may not be in a working state. Please consider submitting a bug report about it.

subprocess installed post-installation script returned error exit status 2


This bad?

---

### Post by donniezazen on 2011-06-02
> **xxhopingtearsxx said:**
> I was upgrading to Ubuntu 11.10 Alpha and I got this error:



This bad?

Depending on what you mean by bad. If it's a production machine then it's a big NO. I went ahead and upgraded with the above error. It aborted itself without cleaning up and messed the source list. After restart desktop was un-usable and later updates broke unity and notification. I am waiting for some update to fix it. Also after upgrade i started getting /udev/run/ error being discussed in other thread.

---

### Post by Harry33 on 2011-06-02
> **xxhopingtearsxx said:**
> I was upgrading to Ubuntu 11.10 Alpha and I got this error:
...
This bad?

The package doc-base is mainly needed by different doc-files.
If you do not need them and do not have ubuntu-desktop meta-package installed, you can safely remove doc-base from your system.

---

### Post by seeker5528 on 2011-06-03
I got some message about a problem with doc-base during installation, but since I was doing the updates in Synpatic I just hit the apply button again once I got back to the main screen and it installed with no complaints the second time around.

Later, Seeker

---

