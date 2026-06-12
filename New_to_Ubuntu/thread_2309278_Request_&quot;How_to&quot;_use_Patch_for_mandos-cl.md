---
title: "Request: &quot;How to&quot; use Patch for mandos-client"
date: 2016-01-09
forum: New to Ubuntu
---

### Post by ruessel on 2016-01-09
Dear Community,

I have installed Ubuntu 14.04 trusty on my Laptop, with encryption.
i am pretty new to Ubuntu, and am a bit confused about how to apply the Patch that was released for the Mandos-client.
I would like to apply it, because i get an error every time I install a package or update. 

Here is a typical error message:
```
gpg: fatal: '/tmp/mandos-keygen-keyrings.4YOxRU579v/trustdb.gpg' can not be opened: File or folder not found
secmem usage: 3424/6848 bytes in 8/19 blocks of pool 7488/65536 
dpkg: error processing package mandos-client (--configure): 
 subprocess installed post-installation script returned error exit status 2 


```



After some research I found following:

[https://bugs.launchpad.net/ubuntu/+source/mandos/+bug/1400145](https://bugs.launchpad.net/ubuntu/+source/mandos/+bug/1400145)

```
=== modified file 'mandos-keygen'
--- mandos-keygen    2014-02-16 13:12:20 +0000
+++ mandos-keygen    2014-03-01 09:51:07 +0000
@@ -228,6 +228,11 @@
     date
     fi
     
+    # Make sure trustdb.gpg exists;
+    # this is a workaround for Debian bug #737128
+    gpg --quiet --batch --no-tty --no-options --enable-dsa2 \
+    --homedir "$RINGDIR" \
+    --import-ownertrust < /dev/null
     # Generate a new key in the key rings
     gpg --quiet --batch --no-tty --no-options --enable-dsa2 \
     --homedir "$RINGDIR" --trust-model always \

```

Could someone make a "How to" step by step, explaining how to apply the above code?
I know how to use the Terminal and the sudo command.


Best Regards, Ruessel

---

### Post by Anwar_Yagoub on 2016-03-22
Hi [COLOR=#000000]ruessel,

If you are still looking to make mandos working with ubuntu 14.04 check this gist:

[/COLOR][https://gist.github.com/AnwarYagoub/2120c3eade1480f6dd3c](https://gist.github.com/AnwarYagoub/2120c3eade1480f6dd3c)

---

