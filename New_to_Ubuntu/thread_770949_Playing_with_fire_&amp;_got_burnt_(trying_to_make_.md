---
title: "Playing with fire &amp; got burnt (trying to make .deb)"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ecs_pf5 on 2008-04-27
[SOLVED]


I decided to try and make a .deb package.

It seemed to worked okay initially, package said it installed and it's name appeared in adept (similar to synaptic but in Kubuntu) but it now looks like my 'test' package has incorrectly formatted postinst and prerm scripts. And he is stuck fast :(

This means I can't reinstall the package nor can I remove it via adept.

I was trying (in my trail and error way) to figure out the postinst and prerm scripts by entering bash commands in them.. is this wrong :confused:

Right now I've got this installed:

package name: testpackage
files installed: just one: /home/fishpants/fishpants-document

control file:

```

Package: testpackage
Version: 0.3
Section: web
Priority: optional
Architecture: all
Essential: no
Installed-Size: 1024
Maintainer: Hans Bistdunass [hans@ruwett.com]
Provides: testpackage
Description: Places a folder in the home directory called fishpants

```postinst and prerm files:

```

#!/bin/sh
# This is a comment!
[couple of very simple commands, touch, redirected echo to a file]

```folder structure used to create package:

BuildFolder/DEBIAN/control
BuildFolder/DEBIAN/postinst
BuildFolder/DEBIAN/prerm
BuildFolder/home/fishpants/fishpants-document

fishpants-document contains just "Hello World!"

.deb package was created by:

```

sudo dpkg -b Desktop/BuildFolder /home/user/Desktop/testpackage.deb

```since my badly-arranged package now seems to be stuck fast like a pig in a hedge, how can I manually remove it.. or find and correct the badness in my postinst and prerm files so that adept can do it's job..

Trying to force removal gives me:

```

user@kubuntu:~$ sudo dpkg --force all -r testpackage
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 99269 files and directories currently installed.)
Removing testpackage ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing testpackage (--remove):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 testpackage
user@kubuntu:~$   

```

here's my /var/lib/dpkg/info/testpackage.list:

```

/.
/home
/home/fishpants
/home/fishpants/fishpants-document

```/var/lib/dpkg/info/testpackage.postinst:

```

(file is blank)

```/var/lib/dpkg/info/testpackage.prerm:

```

(file is blank)

```





--------------


solved by:

kdesu konqueror
- create missing /home/fishpants/fishpants-document

add following to prerm script;

```

#!/bin/sh
unlink /home/fishpants/fishpants-document
rmdir /home/fishpants

```

then run sudo dpkg --force all -r testpackage

---

