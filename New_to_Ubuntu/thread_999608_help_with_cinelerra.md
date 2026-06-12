---
title: "help with cinelerra"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by lad3391 on 2008-12-02
i've tried to follow a couple different guides online, and on the ubuntu forums, and i keep getting the same error. any help?

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libopenexr2c2a (>= 1.2.2) but it is not installable
E: Broken packages

---

### Post by bobnutfield on 2008-12-02
> The following packages have unmet dependencies:
cinelerra: Depends: libopenexr2c2a (>= 1.2.2) but it is not installable
E: Broken packages

First, try to go to Synaptic Package Manager, Edit, scroll down to "fix broken packages".  Then try reinstalling.  OpenEXR is the culprit package and it is usually installed in Ubuntu by default with most multimedia apps.  It is an image file reading format.  libopenexr6 is in the repos.

---

### Post by lad3391 on 2008-12-02
i tried what you said, the bottom left of the screen said "fixed dependency problems"

i tried sudo apt-get install upgrade, followed by sudo apt-get install cinelerra

i got this error
The following packages have unmet dependencies:
  cinelerra: Depends: libopenexr2c2a (>= 1.2.2) but it is not installable
E: Broken packages
thomas@thomas-laptop:~$ sudo apt-get install libopenexr2c2a 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libopenexr2c2a is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libopenexr2ldbl
E: Package libopenexr2c2a has no installation candidate


so i tried to install anything involving openEXR from synaptic, all installed sucessfully except libopenexer2ldbl for the following reasons




ibopenexr2ldbl:

Package libopenexr2ldbl has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

---

