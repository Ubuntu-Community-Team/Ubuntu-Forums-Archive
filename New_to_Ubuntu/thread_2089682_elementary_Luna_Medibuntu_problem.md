---
title: "elementary Luna Medibuntu problem"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by RichieB07 on 2012-11-29
I tried to install Medibuntu, but it threw up the 404 error during install.  Now, when I run Update Manager, it gives this error:

> W:Failed to fetch [http://packages.medibuntu.org/dists/luna/free/source/Sources](http://packages.medibuntu.org/dists/luna/free/source/Sources)  404  Not Found
, W:Failed to fetch [http://packages.medibuntu.org/dists/luna/non-free/source/Sources](http://packages.medibuntu.org/dists/luna/non-free/source/Sources)  404  Not Found
, W:Failed to fetch [http://packages.medibuntu.org/dists/luna/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/luna/free/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://packages.medibuntu.org/dists/luna/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/luna/non-free/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://packages.medibuntu.org/dists/luna/free/binary-i386/Packages](http://packages.medibuntu.org/dists/luna/free/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://packages.medibuntu.org/dists/luna/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/luna/non-free/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

There is no medibuntu-keyring to delete, and I have no idea how to get rid of this error.

Any help would be greatly appreciated.

It's Luna 64bit.

---

### Post by RichieB07 on 2012-11-30
I fixed it by going into Pantheon Files as root, went to /etc/apt/sources.  It brought up the Sources list, and Medibuntu was in there.  I just removed them, and voila, it works again.

---

