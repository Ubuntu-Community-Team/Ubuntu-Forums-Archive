---
title: "Error with Signature Verification"
date: 2011-10-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by fantab on 2011-10-07
I am getting the following error when in *sudo apt-get update*

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://security.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://in.archive.ubuntu.com oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://in.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```The error is with signature verification...I am getting updates though.
**How do I resolve this?**

---

### Post by fantab on 2011-10-08
> **fantab said:**
> I am getting the following error when in *sudo apt-get update*

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://security.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://in.archive.ubuntu.com oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://in.archive.ubuntu.com oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```The error is with signature verification...I am getting updates though.
**How do I resolve this?**

Ok, Now I am getting updates which already have been installed...

---

