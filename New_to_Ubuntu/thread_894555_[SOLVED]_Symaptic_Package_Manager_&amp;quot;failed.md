---
title: "[SOLVED] Symaptic Package Manager &amp;quot;failed to fetch&amp;quot;"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-08-19
When Synaptic Pkg. Mgr. runs a "reload" it hangs at repo 53 of 115 (115 an approximate number as it hangs). After a few moments, I see:

GPG error: [http://apt.byteme.org.uk](http://apt.byteme.org.uk) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 729A79A23B7EE764GPG error: [http://apt.byteme.org.uk](http://apt.byteme.org.uk) experimental Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 729A79A23B7EE764Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/main/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/restricted/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/main/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/main/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/restricted/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/restricted/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/universe/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/universe/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/universe/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/multiverse/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/multiverse/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy/multiverse/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/main/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/main/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/main/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/restricted/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/universe/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/universe/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/universe/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/multiverse/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-updates/multiverse/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/main/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/restricted/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/universe/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/multiverse/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/main/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/main/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/restricted/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/universe/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/universe/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-backports/multiverse/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/main/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/restricted/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/main/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/main/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/restricted/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/restricted/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/universe/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/universe/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/universe/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/multiverse/binary-i386/Packages.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Failed to fetch [http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/multiverse/source/Sources.gz](http://ubuntu.cs.uaf.edu/ubuntu/dists/hardy-security/multiverse/source/Sources.gz)  Unable to connect to ubuntu.cs.uaf.edu http:
Some index files failed to download, they have been ignored, or old ones used instead.

What causes this and how do I fix it?

---

### Post by Elfy on 2008-08-19
All the failed to fetch give me an error as well, try again later unless, this is trying agian later :)

What was the [http://apt.byteme.org.uk](http://apt.byteme.org.uk) for, it would appear that the key is missing.

---

### Post by DR583V3 on 2008-08-19
The [http://ubuntu.cs.uaf.edu](http://ubuntu.cs.uaf.edu) website seems to be down at the moment.

---

