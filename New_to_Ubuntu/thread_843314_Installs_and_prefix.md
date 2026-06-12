---
title: "Installs and prefix"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by traisen on 2008-06-28
I installed gnu classpath via synaptic and now I want to install a newer version locally in my home directory... how can I do this and keep the 2 versions straight?

I can settle for just one version, but want to understand install... since I have problems everytime...
Thanks

---

### Post by traisen on 2008-06-28
Thanks for all who viewed... looks like libtool may hold the answer.


Usage: libtool [OPTION]... --mode=uninstall RM [RM-OPTION]... FILE...

Remove libraries from an installation directory.

RM is the name of the program to use to delete files associated with each FILE
(typically `/bin/rm').  RM-OPTIONS are options (such as `-f') to be passed
to RM.

If FILE is a libtool library, all the files associated with it are deleted.
Otherwise, only FILE itself is deleted using RM.

Try `libtool --help' for more information about other modes.
carlyn@cfj08:~/local$ sudo libtool --help --mode=clean /home/carlyn/local/lib/classpath
Usage: libtool [OPTION]... --mode=clean RM [RM-OPTION]... FILE...

Remove files from the build directory.

RM is the name of the program to use to delete files associated with each FILE
(typically `/bin/rm').  RM-OPTIONS are options (such as `-f') to be passed
to RM.

If FILE is a libtool library, object or program, all the files associated
with it are deleted. Otherwise, only FILE itself is deleted using RM.

Try `libtool --help' for more information about other modes.

---

