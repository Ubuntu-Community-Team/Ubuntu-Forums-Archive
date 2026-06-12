---
title: "Password manager with generator"
date: 2017-05-08
forum: New to Ubuntu
---

### Post by vineyridge on 2017-05-08
Did one come with Ubuntu?  I've looked at Password Gorilla and Passwords and Keys and neither come with a generator.

I also looked at LastPass and am unwilling to accept their terms of service.  So that seems to leave me with KeePassx.  Are there others?
Installing KeePassX requires expanding a tarball.  I'm assuming .tar is the equivalent of the Windows .zip.

How do I do that?  I've searched the Desktop Guide for the following topics: compressed files, tarball, and tar and nothing comes up.

---

### Post by slickymaster on 2017-05-08
You have [pwgen]("http://packages.ubuntu.com/zesty/debian-installer/pwgen-udeb") and [apg]("http://packages.ubuntu.com/zesty/debian-installer/pwgen-udeb") in the repos.

And if you don't want do install anything, you can always run in a terminal window the following```
echo `< /dev/urandom tr -dc _A-Z-a-z-0-9 | head -c6`
```Change "-c6" to the length of password you want.

Also, have a read at [https://help.ubuntu.com/community/StrongPasswords](https://help.ubuntu.com/community/StrongPasswords)

---

### Post by vineyridge on 2017-05-08
I'm a complete terminal novice.  

The problem is that I completely freeze up when asked to generate a password;  if I can remember it, it's too weak.  

I've downloaded and installed pwgen through the Software manager, but still would like to look at KeePassX which seems far more sophisticated.  I've downloaded the .tar.gz file.  What do I do next?  I can't use apt-get until it is expanded, can I?

---

### Post by kc1di on 2017-05-08
you can install pwgen also will give many differing PWs.
once installed go to terminal and type ```
pwgen
```
also you can type ```
pwgen --help 
``` or ```
man pwgen
```
for further options.

---

### Post by howefield on 2017-05-08
> **vineyridge said:**
> ...but still would like to look at KeePassX which seems far more sophisticated.  I've downloaded the .tar.gz file.  What do I do next?  I can't use apt-get until it is expanded, can I?

Keepassx is included in the Ubuntu repositories so should be an easy enough install, shouldn't be a need to download a tar.gz file.

---

### Post by litlesam on 2017-05-08
Keepass2 is included in the Ubuntu repositories as well.

---

### Post by The Cog on 2017-05-08
> **howefield said:**
> Keepassx is included in the Ubuntu repositories so should be an easy enough install, shouldn't be a need to download a tar.gz file.

Ignore the tar file. This command will install it from the repositories as howefield suggests:
```
sudo apt install keepassx
```

---

### Post by mastablasta on 2017-05-09
another option is keepass2 also in repos and should be in software center: [SIZE=2]https://apps.ubuntu.com/cat/applications/quantal/keepass2/
[/SIZE]

---

### Post by howefield on 2017-05-09
I might add that you do not mention which version of Ubuntu you are using, if you are on 14.04 I probably wouldn't use the included Keepassx package which is version 0.4.3 but any supported release later than 14.04 should be ok with 2.0.2 or 2.0.3.

---

### Post by HermanAB on 2017-05-09
Well, if you are concerned about security, then don't ever install random cruft from tar balls.  KeepassX is in the repos, as mentioned above.

---

