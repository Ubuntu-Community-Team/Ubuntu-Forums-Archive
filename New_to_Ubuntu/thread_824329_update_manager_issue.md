---
title: "update manager issue"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by harry rao on 2008-06-10
hi,
i have an issue with software updates.

Whenever i try to update my software sources the following message comes up, however i'm able to update whenever i'm at uni :

```
"W: Failed to fetch http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/awn-testing/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_AU.bz2  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_AU.bz2  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_AU.bz2  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Failed to fetch http://au.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_AU.bz2  Could not connect to localhost:8080 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead."
```
[B]
could someone please help me to change the settings?
[/B]
p.s. i've already commented out the uni repositories.

---

### Post by PmDematagoda on 2008-06-10
Seems like you may have some proxy settings active that prevent apt-get from connecting, take a look at the proxy settings and see if they are right(or if they should exist at all).

---

### Post by harry rao on 2008-06-10
i checked in the network proxy preferences and 'direct internet connection' is selected...

---

### Post by iaculallad on 2008-06-10
On your terminal:

```
unset http_proxy
sudo apt-get update
```

---

### Post by harry rao on 2008-06-10
that was perfect.
thank you.

---

