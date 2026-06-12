---
title: "GPG/PGP Failed to Fetch, etc."
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-08-13
Every time I do an update I see a box saying:

GPG error: [http://apt.byteme.org.uk](http://apt.byteme.org.uk) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 729A79A23B7EE764GPG error: [http://apt.byteme.org.uk](http://apt.byteme.org.uk) experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 729A79A23B7EE764Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  503 Service Temporarily Unavailable [IP: 78.46.39.176 80]
Some index files failed to download, they have been ignored, or old ones used instead.


I've had similar messages since Breezy Badger (not the above pkg. however)
All I really want is to get this fixed. Once and for all. I've looked around for a simple fix. I don't need Seahorse or similar. I just want to know how to tell the 'puter that new sofware is coming from a non-Canonical repo and it's safe to load it, etc, so I don't get (@# $RV234 these blinking eternal) error messages.

---

### Post by iaculallad on 2008-08-13
Try to change your download server on Software Sources, try using the Main Server instead.

---

### Post by Mark_in_Hollywood on 2008-08-13
Nope! Same error message(s)

---

### Post by iaculallad on 2008-08-13
You could try relating with this [page]("https://bugs.launchpad.net/medibuntu/+bug/252271") from launchpad.

---

