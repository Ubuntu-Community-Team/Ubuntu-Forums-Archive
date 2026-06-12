---
title: "[SOLVED] Problem Updating packages"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Jazzy_Jeff on 2008-07-01
Hello, I am trying to update packages from all sources and I get the following error message:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

How can I fix this. Thank you.

---

### Post by drs305 on 2008-07-01
Run the following for hardy:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

If that doesn't work, you may need to reload your medibuntu repository:
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

For other versions, visit the Medibuntu page:
[Repository Howto]("http://www.medibuntu.org/repository.php")

---

### Post by Jazzy_Jeff on 2008-07-01
[QUOTE=drs305;5301818]Run the following for hardy:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update

```

Worked like a charm. Thanks for the quick reply.

---

### Post by iaculallad on 2008-07-01
Another work-around: Navigate to System->Administration->Software Sources, "Ubuntu Software" tab, Change the "Download From:" to use "Main Server". Click on Close button and open your terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

EDIT: Disregard, Late reply.

---

