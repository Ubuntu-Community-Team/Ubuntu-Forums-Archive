---
title: "How to compile my own (newer) version of a program?"
date: 2008-07-27
forum: Packaging and Compiling Programs
---

### Post by BernardSRoberts on 2008-07-27
Hello,

I am sure this is a common question, but I searched and could not find the answer.  (I'm not a programmer, just a user.)

Background:

I am trying to use a couple of programs that are in the Ubuntu repository.

However, the "Ubuntu versions" are a bit out of date, and I am being bitten by bugs that render these versions not usable to me.

(Yes, bugs have been filed on Launchpad requesting a version bump.)

With, at least one of the programs, i was able to "compile from source" by following the README.  (make, etc.)  

The Question:

Assuming I can get the program to compile on Ubuntu, how can I integrate my new version into the regular package management system so that I will be notified when/if an updated "officially supported" package is released?

Obviously I'd like the option of declining the new "official package" should the bug in question not yet be fixed.


Thank you  :)

---

### Post by jay019 on 2008-07-27
Install an app called checkinstall.

This will help you to create and install the app as a .deb file that will show up in synaptics making it a snap to remove. Not sure it will notify you of any updates though, but makes it easier to see in synaptics if you are running an earlier or later version than the one in the repos.

HTH

---

### Post by BernardSRoberts on 2008-07-27
Thanks for the checkinstall (and auto-apt) lead. Interesting stuff.

How do I mark the package as being a temporary replacement for the original? 

That is:

1) It will satisfy the dependency of secondary, otherwise functional, packages.
2) Newer versions in the repository will prompt me to manually approve/disapprove a return to the officially supported packages.

(#1 being the more important.)

---

### Post by jay019 on 2008-07-28
Im not sure that it is possible. Sorry. 

Maybe someone more knowledgable than me may have a different answer?

---

### Post by LinuxRocks713 on 2008-07-28
> **BernardSRoberts said:**
> Thanks for the checkinstall (and auto-apt) lead. Interesting stuff.

How do I mark the package as being a temporary replacement for the original? 

That is:

1) It will satisfy the dependency of secondary, otherwise functional, packages.
2) Newer versions in the repository will prompt me to manually approve/disapprove a return to the officially supported packages.

(#1 being the more important.)

In your DEBIAN/control, add

Provides: *Outdated ubuntu package*
Depends: Existing depenencies... ,dialog

In your DEBIAN/postinst, add

dialog --msgbox "This is an unofficial version of *foobar*. Please return to the official version when it is updated."

In your DEBIAN/prerm, add

dialog --msgbox "You are removing the unofficial version of *foobar*. Please return to the official version after this uninstallation."

---

