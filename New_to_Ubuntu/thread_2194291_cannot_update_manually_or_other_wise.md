---
title: "cannot update manually or other wise"
date: 2013-12-17
forum: New to Ubuntu
---

### Post by tastyham on 2013-12-17
I get this message:  W:Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thoughts?

---

### Post by QIII on 2013-12-17
Hello!

Medibuntu was deactivated some time ago.  You'll need to remove it from your sources.

---

### Post by deadflowr on 2013-12-17
You need to disable the medibuntu repos, as they are no longer open/exist.

Either edit and add a comment (#) to the entry in the sources.list file, or
Open the update manager and go to settings(it's in the bottom left of update manager)
then when the software sources window opens, go to other software.
Find the medibuntu entries and uncheck them.(it'll need your password to make the changes)
then close and while still in the update manager, press the check button to reload the package lists.

---

