---
title: "Why I cant update???"
date: 2009-01-22
forum: Philippine Team
---

### Post by darkzlayer on 2009-01-22
I have reinstalled ubuntu. But after reinstalling it, it wont update anymore

Here's the error message 
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com intrepid-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://ph.archive.ubuntu.com intrepid-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/intrepid-security/Release  

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

How can I get rid of this error?

---

### Post by dannybuntu on 2009-01-22
Hello, please post your /etc/apt/sources.list

---

### Post by darkzlayer on 2009-01-22
> **dannybuntu said:**
> Hello, please post your /etc/apt/sources.list

Where can I see that? I'm totally a linux noob :(

---

### Post by loell on 2009-01-22
your sources.list is ok, or should be ok, since you did not touch it.

it is found at  **/etc/apt/sources.list**

it's caused by a bad proxy in the repository server, anyhow, try updating in a few hours or so.


-edit

also do..

sudo apt-get clean
sudo apt-get update

---

### Post by darkzlayer on 2009-01-22
> **loell said:**
> your sources.list is ok, or should be ok, since you did not touch it.

it is found at  **/etc/apt/sources.list**

it's caused by a bad proxy in the repository server, anyhow, try updating in a few hours or so.

Ok thanks guys for replying...
I think I will change my download server to Main server at this moment..So that I could use this PC later:D

---

