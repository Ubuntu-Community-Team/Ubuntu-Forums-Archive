---
title: "[SOLVED] Updater gets stuck (8.10)"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by GreyArea2 on 2008-11-02
Hello again.

Whenever I check for updates (using Update Manager), everything goes smoothly until file 20 of 29. Then it just freezes up, refusing to go any further; the download rate is unhelpfully listed as "unknown". After a few minutes, it gives up, giving me a lengthly error message.

The error:
```
W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg  Could not connect to ca.archive.ubuntu.com:80 (129.97.134.71), connection timed out

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_CA.bz2  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_CA.bz2  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_CA.bz2  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_CA.bz2  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_CA.bz2  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_CA.bz2  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_CA.bz2  Unable to connect to ca.archive.ubuntu.com http:

W: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_CA.bz2  Unable to connect to ca.archive.ubuntu.com http:

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Things I've tried:
- Disabling all "Third-Party Software" in "Software Sources"; this just causes it to get stuck at file 15 of 20, or something like that.

- Rebooting the computer; doesn't change a thing.

Thanks for any help.

---

### Post by taurus on 2008-11-02
I recall somebody said something about the Canadian site is down or something like that.  Try changing to another server and see if it would update now.

---

### Post by GreyArea2 on 2008-11-02
How do I change my server? Also, when can we expect the Canadian site to work again?

---

### Post by taurus on 2008-11-02
System -> Administration -> Synaptic Package Manager.  There is an option to pick another server from that window.

---

### Post by GreyArea2 on 2008-11-02
Excellent, got it. Thank you. :)

---

