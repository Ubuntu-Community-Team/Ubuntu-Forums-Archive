---
title: "oneiric signature verification problem"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ptn107 on 2011-09-30
*sudo apt-get update* yields:
```
W: GPG error: http://security.ubuntu.com oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: http://us.archive.ubuntu.com oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/oneiric/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
```

I purged and reinstalled ubuntu-keyring and ubuntu-extras-keyring with no success.

---

### Post by douham on 2011-09-30
I have had a problem updating from main server a few hours ago, changing to another fairly up-to-date repository and updating from there seems to have resolved the issue.
edit; check the mirror list [here]("https://launchpad.net/ubuntu/+archivemirrors")

---

### Post by Heero_Yuy_X on 2011-10-01
tried selecting the "best server" in Software Sources, still having signature errors.

I remember once I imported the keys one by one, it worked for a while but gave me errors two days later... :(


Edit : Finally ! this worked for me : [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html]("http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html")

---

### Post by ptn107 on 2011-10-01
The solution was to:
```
sudo rm -r /var/lib/apt/lists
sudo mkdir -p /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by Heero_Yuy_X on 2011-10-02
mark as solved? :popcorn:

---

