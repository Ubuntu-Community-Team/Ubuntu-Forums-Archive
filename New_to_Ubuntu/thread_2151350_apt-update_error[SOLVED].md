---
title: "apt-update error[SOLVED]"
date: 2013-06-04
forum: New to Ubuntu
---

### Post by Bapun007 on 2013-06-04
I am using ubuntu 12.10 , today when i try to update it failed ttelling me to use commandline . when i use apt-get update i get this error-

```
W: GPG error: http://deb.opera.com stable Release: The following signatures were invalid: BADSIG E585066A30C18A2B Opera Software Archive Automatic Signing Key 2013 <packager@opera.com>
W: Failed to fetch http://packages.medibuntu.org/dists/quantal/Release.gpg  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)

W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/quantal-getdeb/Release.gpg  Something wicked happened resolving 'screenshots.getdeb.net:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Please help

---

### Post by slickymaster on 2013-06-04
Try this:
```
$ sudo -i
 # apt-get clean
 # cd /var/lib/apt
 # mv lists lists.old
 # mkdir -p lists/partial
 # apt-get clean
 # apt-get update
```

---

### Post by Bapun007 on 2013-06-04
Thanks for help. it now works

---

