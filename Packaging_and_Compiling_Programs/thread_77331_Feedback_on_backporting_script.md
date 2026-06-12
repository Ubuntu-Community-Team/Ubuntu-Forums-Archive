---
title: "Feedback on backporting script"
date: 2005-10-16
forum: Packaging and Compiling Programs
---

### Post by ow50 on 2005-10-16
I have made a backporting script, it's available at
[http://koti.mbnet.fi/~ots/scripts/debbin](http://koti.mbnet.fi/~ots/scripts/debbin)

The script will build debian packages from debian sources. For example, I have used it to build stuff from Marillat and Debian Mentors, stuff that is not available for Ubuntu. And when Dapper get's ahead of Breezy, I'll use it for backporting newer versions to Breezy.

I'd like some feedback before posting it as a HOWTO. Especially on the commands defined in the "configure_commands" function, the changelog entry and the package version numbering (the ~ trailer). Also on any changes needed to make it easier to use.

To try the script, first install the package "devscripts" and then edit the settings at the start of the script. After that run "debbin --help" to check the usage info.

---

### Post by ow50 on 2005-10-18
Updated with package gpg-signing and dput-uploading.

---

### Post by AgenT on 2005-10-18
Is there not an official script that does this already? Not exactly sure where one can find it, but it should be public and available somewhere. Or maybe your script is an improvement.

---

### Post by ow50 on 2005-10-18
[QUOTE=AgenT]Is there not an official script that does this already? Not exactly sure where one can find it, but it should be public and available somewhere. Or maybe your script is an improvement.[/QUOTE]
Perhaps you mean the ubp-build.py by jdong
[http://backports.ubuntuforums.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py](http://backports.ubuntuforums.org/ubp/projects/ubp-tools/ubp-build/ubp-build.py)

And yes, my script is an improvement in some areas and a de-improvement, or a simplification, in other areas.

---

