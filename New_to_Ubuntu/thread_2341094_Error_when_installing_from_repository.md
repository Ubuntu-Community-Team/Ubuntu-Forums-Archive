---
title: "Error when installing from repository"
date: 2016-10-24
forum: New to Ubuntu
---

### Post by phonicdev2 on 2016-10-24
having an issue when attempting to install packages from the repository, so far pthon, idle, and a couple other things worked out fine, but anything over the last couple days has come back with the same errors:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 inkscape : Depends: libpoppler58 (>= 0.41.0) but it is not installable
            Recommends: libwmf-bin but it is not going to be installed
            Recommends: perlmagick
            Recommends: python-lxml but it is not going to be installed
            Recommends: python-uniconvertor but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Any clues? thanks all.

---

### Post by ian-weisser on 2016-10-24
Looks like a version conflict to me.
You installed something that replies upon a different version of some dependency.
This usually occurs when you install non-Ubuntu software from PPA or other non-Ubuntu sources which pull-in wrong-version dependencies.

One easy way to resolve the problem is to uninstall the offending software (including all the non-Ubuntu dependencies) and to disable the offending source.

---

### Post by phonicdev2 on 2016-10-24
I've removed a few potential programs following your advice, atom, deluge, and something else :/ but still no joy.
is there a way to find which program is causing the issue?

---

### Post by phonicdev2 on 2016-10-24
Fixed :) Had to do it outside of terminal and go into the settings window but its working fine now

Thank you!

---

### Post by ian-weisser on 2016-10-24
Glad to see you got it fixed.

---

