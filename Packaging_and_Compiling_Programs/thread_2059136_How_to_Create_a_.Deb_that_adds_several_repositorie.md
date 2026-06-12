---
title: "How to Create a .Deb that adds several repositories and install several packages."
date: 2012-09-17
forum: Packaging and Compiling Programs
---

### Post by lewisgoddard on 2012-09-17
I am looking to create a single .Deb package.

I am not interested in signing, uploading to sourceforge, launchpad, or adding it to any form of package management system.

I want it to add several (defined: more than one) PPAs, check for updates, and install several (again, more than one) packages.

I looked at Meta-packages (which originally seemed to be what i was after), but am now confused as to the abilities of running a script before installation.

I have looked at the source of the getdeb.net packages (which add a software source) but would prefer to add the with a script running (for example) ```
sudo add-apt-repository -y ppa:skype-wrapper/ppa && sudo apt-get update
```, rather than what they do, which appears to be include a copy of a software sources list and simply copy it over (then update and install with the dependencies).

I would prefer a .Deb than a simple script file because it's one less step for the user (marking as executable).

Any help (direction to a similar package would be brilliant) would be much appreciated.

---

