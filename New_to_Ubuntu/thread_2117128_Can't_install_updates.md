---
title: "Can't install updates"
date: 2013-02-17
forum: New to Ubuntu
---

### Post by Stephenkboyer on 2013-02-17
Hello anyone,

Can someone help me out with this?  
I keep getting a notice for updates but when I try to install them it fails.  Here is the details for update manager:   

Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine1.5_1.5.19-0ubuntu3_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine1.5_1.5.19-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine1.5-i386_1.5.19-0ubuntu3_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine1.5-i386_1.5.19-0ubuntu3_i386.deb) 404  Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic-pae_3.2.0.35.40_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic-pae_3.2.0.35.40_i386.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic-pae_3.2.0.35.40_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic-pae_3.2.0.35.40_i386.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic-pae_3.2.0.35.40_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic-pae_3.2.0.35.40_i386.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-35.55_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-35.55_i386.deb) 404  Not Found [IP: 91.189.92.200 80]
Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine_1.5.19-0ubuntu3_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine_1.5.19-0ubuntu3_i386.deb) 404  Not Found

---

### Post by schragge on 2013-02-17
Open a terminal, and try
```

sudo apt-get clean
sudo apt-get update

```

---

### Post by Stephenkboyer on 2013-02-17
Thanks Schragge,

That seemed to do the trick.

---

### Post by deadflowr on 2013-02-17
First off, I'd simply uncheck and remove the ubuntu-wine ppa in Software Sources. (It's in the other software section)

Second, I'd post the results from
```
cat /etc/apt/sources.list
```

And please use the code tags in the reply box toolbar(it's the # symbol)

Edit: Seems you got it fixed then. If the problems come back post again.

---

### Post by schragge on 2013-02-17
@**deadflowr**. There was no need to remove PPA. I followed the link from the error message, and the referenced deb was already replaced by the newer version in the PPA, yet the APT package databank was still not updated. Attempt to retrieve the non-existing deb naturally caused error 404.

---

