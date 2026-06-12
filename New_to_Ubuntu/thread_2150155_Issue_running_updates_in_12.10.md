---
title: "Issue running updates in 12.10"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by androssofer on 2013-05-31
Hi Guys,

So this morning I can't get my updates to run. I get the error:

> Reading package lists... Error!
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 8771ADB0816950D8
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_quantal-security_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

I read a few other posts on this but none seem to work. 

I did:

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8771ADB0816950D8
```

but that had no effect. So tried: 

```
rm /var/lib/apt/lists/* -vf
apt-get clean
apt-get update
```

but again get the same error. Any ideas?

---

