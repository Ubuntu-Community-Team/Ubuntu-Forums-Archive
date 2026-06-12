---
title: "repo updating is not working."
date: 2006-06-15
forum: Repositories &amp; Backports
---

### Post by czedlitz on 2006-06-15
This is confusing me, and i am not sure how to correct it.  I was able to update fine 2 days ago, but last night i tried to update the repo indexes and it errors out.  i get this after i open Synaptic and then press Reload.  It then counts up the number of repos it has to download which is odd, i thought it was a set number to index.  stops at 27 of 51 and then gives this error:
```

[SIZE="2"]http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg: Connection failed [IP: 85.133.25.8 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg: Connection failed
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg: Connection failed [IP: 85.133.25.8 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz: Connection failed
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz: Connection failed
http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz: Connection failed
http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80]
http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz: Connection failed [IP: 85.133.25.8 80][/SIZE]

```

Now, if i goto that IP address, it's an ubuntu apache server, but there is nothing else in the directory listing... so i am not sure why it's looking there and how to chage this.  I appreciate any help.  Thanks!

---

### Post by czedlitz on 2006-06-15
Here is almost the same thing, but this is the result when i do a apt-get update

```
[SIZE="2"]root@lappy486:/home/chris# apt-get update
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper-backports Release
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/main Sources
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Packages
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Sources
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Packages
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection faile d [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connecti on failed [IP: 85.133.25.8 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connec tion failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Connec tion failed [IP: 85.133.25.8 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Pa ckages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i 386/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources .gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/S ources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i38 6/Packages.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packag es.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sou rces.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Conne ction failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages .gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz  C onnection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packag es.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Pack ages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i38 6/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.g z  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sou rces.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Pa ckages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i 386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i38 6/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i 386/Packages.gz  Connection failed [IP: 85.133.25.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@lappy486:/home/chris#[/SIZE]

```

Please help, this is crazy!

---

### Post by czedlitz on 2006-06-15
Ok i figured it out, my router was not allowing it. so nevermind :)

---

### Post by Bernie01 on 2006-06-15
[QUOTE=czedlitz]Ok i figured it out, my router was not allowing it. so nevermind :)[/QUOTE]

I have been having similar problems. How did you overcome your router getting in the way?

---

### Post by HUTT on 2006-06-16
I have these same problems can you please let me know how you fixed this?

-Will

---

### Post by ORF1000 on 2006-06-18
Dapper must be a dirty word.  I turned off keyword blocking and ... it worked!

---

### Post by ihitf13anddied on 2006-06-18
wow....thought you were full of it. i own a netgear WGT624v3 router, and I tried to update for about 40 minutes, with no luck. Then i read your post, disabled keyword blocking, and presto! it worked. thanks a bunch.


~Chris

---

### Post by Luddy on 2006-06-28
Wow you weren't lying I didn't even think I had keyword word blocking on.  I spent so many hours trying to figure this problem out, and had a feeling it was the router all along.

e-cookie for you.=D>

---

### Post by rexjutlandiae on 2006-07-03
I had the exact same problem, and also used HOURS trying to find the cause.

My router is a Netgear WGR614, and with "Keyword blocking" disabled the problem disappears.

The error occurs both using apt-get from commandline and the GUI-based update-tools (Applications|Add/remove and System|Administration|Software Preferences).

When using the software tools, the error is "connection failed", similar to above.

Thanks for the help!

---

### Post by programgeek on 2006-07-04
Hey, I posted my problem (I believe it's the same as yours) over here:

[http://www.ubuntuforums.org/showthread.php?t=208627](http://www.ubuntuforums.org/showthread.php?t=208627)

I would assume as of now it's a router problem, and possibly something my firmware isn't ready for, so back to basic stuff I suppose.. Very insightful article, If you use a WRT54G and know a workaround, I would be greatful if you could notify me.

Thanks!

---

### Post by amethyst00 on 2006-07-17
Hi to everyone !
The tip is interesting but it doesn't concern all the routers. The mine (D-Link DSL-G604T) hasn't this feature. 
Beside this the router doesn't support the ipv6 protocol. I ought to desactivate all the entries ipv6 in Ubuntu.
Furthermore the router doesn't manage correctly the DNS. It is useful to desactivate this service in the router and to enable only Ubuntu to do it.
These two conditions allow the apt-get updates.

I hope this helps some people.

amethyst

---

