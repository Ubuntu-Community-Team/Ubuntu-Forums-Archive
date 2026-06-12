---
title: "Unable to upload home-made packages to my ppa"
date: 2008-08-11
forum: Packaging and Compiling Programs
---

### Post by DaneM on 2008-08-11
Hello.

I've compiled some packages and would like to put them up on my ppa.  I've followed the directions on [https://help.launchpad.net/PPA](https://help.launchpad.net/PPA) , but whenever I try to upload my packages, I get the following:

```

dane@Orchestrator:~/Empathy$ dput danes-ppa
empathy_2.23.6-1_amd64.changes
Checking Signature on .changes
gpg: no valid OpenPGP data found.
gpg: the signature could not be verified.
Please remember that the signature file (.sig or .asc)
should be the first file given on the command line.
No signature on /home/dane/Empathy/empathy_2.23.6-1_amd64.changes.

```

Here's my ~/dput.cf:

```

[danes-ppa]
fqdn = ppa.launchpad.net
method = ftp
incoming = ~dmutters/ubuntu/
login = anonymous
allow_unsigned_uploads = 0

```

I used (in the source directory) "debuild -S -k<key>" to make the source package, and then "sudo pbuilder --build ../whatever.dsc" to compile for amd64 arch.  Somebody on IRC suggested that I need to upload source-only packages, and cannot upload any binaries; I don't know whether that's true, or how to do it.

I would appreciate any help you can provide.

--Dane

---

### Post by viciouslime on 2008-08-11
You need to run "debuild -S -sa" if the package you're building doesn't currently exist in the ubuntu repos, or "debuild -S -sd" if there is some version of it in there already.

The IRC person is correct, you can only upload source packages, launchpad will then build deb files for every supported architecture for you.

---

### Post by DaneM on 2008-08-11
Thanks for the reply.  I'll give that a shot.

---

