---
title: "install csh"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by jiangchongyi on 2012-04-22
Hello, 
 
I tried to install a program by following the provided instruction:
 
[COLOR=#52594f]$> sudo apt-get [COLOR=#52594f]install csh[/COLOR][/COLOR]
[COLOR=#52594f][COLOR=#52594f][/COLOR][/COLOR] 
[COLOR=#52594f][COLOR=#52594f]but when I keyed in the command above and the password, the following information came up:[/COLOR][/COLOR]
[COLOR=#52594f][COLOR=#52594f][/COLOR][/COLOR] 
[COLOR=#52594f][COLOR=#52594f]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package csh is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source[/COLOR][/COLOR]
[COLOR=#52594f][COLOR=#52594f][/COLOR][/COLOR] 
[COLOR=#52594f][COLOR=#52594f]what is the problem? And how can I fix it?[/COLOR][/COLOR]
[COLOR=#52594f][COLOR=#52594f]Any help will be appreciated&#65281;[/COLOR][/COLOR]
[COLOR=#52594f][COLOR=#52594f][/COLOR][/COLOR]

---

### Post by oldos2er on 2012-04-22
Try running ```
sudo apt-get update
``` first.

---

### Post by jiangchongyi on 2012-04-22
> **oldos2er said:**
> Try running ```
sudo apt-get update
``` first.
 
 
I do as your suggestion, but the following comes up:
 
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  Hash Sum mismatch
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-i386/Packages.gz)  Hash Sum mismatch
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-i386/Packages.gz)  Hash Sum mismatch
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/binary-i386/Packages.gz)  Hash Sum mismatch
E: Some index files failed to download, they have been ignored, or old ones used instead.

So what should I do with such situation?

---

### Post by oldos2er on 2012-04-23
Maverick is no long supported, so I'm not sure this will work, but you could try changing servers. [https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

---

