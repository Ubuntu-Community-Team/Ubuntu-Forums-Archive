---
title: "Packaging repo definition and packages in a meta-package"
date: 2013-05-21
forum: Packaging and Compiling Programs
---

### Post by brunson on 2013-05-21
I want to create a meta-package that pulls packages from a third party repo, but I'm new to .deb and don't know if I can do what I want in a single package.

I need to add the PPA to /etc/apt/sources.list.d (simple), then I want to specify a set of packages from that PPA to be installed as dependencies to my package (standard meta-packaging).  I thought I could brute force it by creating the repo.list file and doing apt-get update in a preinst script, but then the repo.list file isn't be tracked in the dpkg database and update fails because of the lock held by the install process.

Is there any way to accomplish this or am I stuck doing it in two steps?

Thanks,
e.

---

### Post by cipherboy_loc on 2013-05-21
Take a look into the preinst script:
[http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html](http://www.debian.org/doc/manuals/debian-faq/ch-pkg_basics.en.html)

In theory, you could do something like:

```

#!/bin/bash

# Double check root...

if [[ $EUID -ne 0 ]]; then
  echo "This script must be run as root" 1>&2
  exit 1
else
  # Then add a repository the standard way.
  apt-add-repository **<repository>**

  # And now you could just install the packages here.
  apt-get install **<packages>**
fi


```

And have the dependencies be apt... However, I don't think you can require an external PPA and have package dependencies from them, as the dependencies download first before preinst or anything else is run...

However, personally I would advise against this except for private use, as it is definitely not the best way to do things and is quite ugly. 



Thanks,
Cipherboy LOC

---

