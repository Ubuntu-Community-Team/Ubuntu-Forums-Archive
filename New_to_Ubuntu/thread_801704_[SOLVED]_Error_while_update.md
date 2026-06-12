---
title: "[SOLVED] Error while update"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by sharks on 2008-05-20
When i update using this sudo apt-get update this error is shown at last:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

---

### Post by iaculallad on 2008-05-20
On the terminal issue this commands:

**If you're using Ubuntu 7.10 "Gutsy Gibbon":**

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list


**If you're using Ubuntu 8.04 "Hardy Heron":**

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

**Then, add the GPG Key:**

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

---

### Post by Maestro23 on 2008-05-20
Add the key for Medibuntu.

[https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu](https://help.ubuntu.com/community/Medibuntu?highlight=(Medibuntu))

---

### Post by sharks on 2008-05-20
Thanks.

---

