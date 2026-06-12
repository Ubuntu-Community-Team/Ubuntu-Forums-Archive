---
title: "Update Manager"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sammiev on 2011-10-08
Hi folks, I'm updating fine at least twice a day but update manager shows I haven't updated in 8 days. This started after one of the updates last week. Anyone else?

---

### Post by praveenthivari on 2011-10-08
No. Update manager works perfectly fine here. Just updated and it reports it correctly.

---

### Post by sammiev on 2011-10-08
I UN-installed from my system and installed it again. It made no difference. :(

---

### Post by crdlb on 2011-10-08
I checked the code, and update-manager looks at the mtime of /var/lib/apt/periodic/update-success-stamp . Searching the web for that path, I found an old bug report: [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/188127](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/188127) . If your situation is the same, then there is a repository in your sources that is failing to update. Run sudo apt-get update in a terminal, and check for failing repositories.

---

### Post by sammiev on 2011-10-08
Correct you are. Thank You.

Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

I decided to restore from backup as I have more than one laptop with all the same settings and this one is the only one with this error. All software sources match, must of had a bad update 8 days a go.
Glad for my USB HD. :)

---

