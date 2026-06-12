---
title: "Fixing a gone bad setup"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Accinson on 2008-06-08
Hi,
some days ago,while trying to play a little bit with Eclipse i had to install the JDK.Being a newbie,i selected a bunch of java-related stuff but something went wrong with two packages,which were not essential for my purposes but that are still bothering me whenever i install a new package,i.e. i get the following output:
```
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
```
After that i type NO+enter and the install succeeds,but this message comes out every single time....
How can i fix this?

---

### Post by Vadi on 2008-06-08
Remove the 'sun-java6-doc' package with 'sudo apt-get remove sun-java6-doc', then it should stop complaining. If you'd still like it, try reinstalling after - and if the issue persists, report this bug, as it'll be an issue in how the package was made then.

---

