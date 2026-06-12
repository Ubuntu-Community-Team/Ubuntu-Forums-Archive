---
title: "Reps down?"
date: 2006-06-03
forum: Repositories &amp; Backports
---

### Post by qalimas on 2006-06-03
I'm trying to apt some software, but when I run the apt-get update NONE of my reps are fetched, every last one fails ><

```
Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 85.133.25.7 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.7 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Err http://archive.ubuntu.com dapper-backports Release.gpg
  Connection failed [IP: 85.133.25.7 80]
Get:1 ftp://cipherfunk.org dapper Release.gpg [189B]
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper-updates Release
Hit ftp://cipherfunk.org dapper Release
Err ftp://cipherfunk.org dapper Release
  
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper-backports Release
Get:2 ftp://cipherfunk.org dapper Release [1387B]
Ign http://security.ubuntu.com dapper-security/universe Packages
Ign http://archive.ubuntu.com dapper/main Packages
Ign ftp://cipherfunk.org dapper Release
Ign http://security.ubuntu.com dapper-security/multiverse Packages
Ign http://archive.ubuntu.com dapper/restricted Packages
Get:3 ftp://cipherfunk.org dapper/main Packages
Ign http://security.ubuntu.com dapper-security/universe Sources
Ign http://archive.ubuntu.com dapper/main Sources
Ign ftp://cipherfunk.org dapper/main Packages
Ign http://security.ubuntu.com dapper-security/multiverse Sources
Ign http://archive.ubuntu.com dapper/restricted Sources
Hit ftp://cipherfunk.org dapper/main Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Packages
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Packages
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://archive.ubuntu.com dapper/universe Sources
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Ign http://archive.ubuntu.com dapper/multiverse Sources
Err http://security.ubuntu.com dapper-security/universe Packages
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/multiverse Packages
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Err http://security.ubuntu.com dapper-security/universe Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Sources
Err http://security.ubuntu.com dapper-security/multiverse Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/main Packages
Ign http://archive.ubuntu.com dapper-backports/restricted Packages
Ign http://archive.ubuntu.com dapper-backports/universe Packages
Ign http://archive.ubuntu.com dapper-backports/multiverse Packages
Ign http://archive.ubuntu.com dapper-backports/main Sources
Ign http://archive.ubuntu.com dapper-backports/restricted Sources
Ign http://archive.ubuntu.com dapper-backports/universe Sources
Ign http://archive.ubuntu.com dapper-backports/multiverse Sources
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/universe Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/multiverse Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/universe Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper/multiverse Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/main Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/restricted Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/universe Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Packages
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/main Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/restricted Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/universe Sources
  Connection failed [IP: 85.133.25.7 80]
Err http://archive.ubuntu.com dapper-backports/multiverse Sources
  Connection failed [IP: 85.133.25.7 80]
Fetched 1576B in 16s (96B/s)
Reading package lists...

```

---

### Post by otakurx on 2006-06-08
I am getting the same thing, is there a work around or something?  I can ping the IP but none of the add/remove software pkgs can see it.  I even manually surfed there and was like "there it is" but yet still the same connection failed messages.

---

### Post by mattwestm on 2006-06-08
Same problem over here too. I have been having this problem for a few days now. Although when I go to the IP in firefox, it works fine.

---

### Post by sixthsiren on 2006-06-08
Whew!!! I thought it might just be. I've been going at this all day and I'm having the exact same errors going on. I thought it was probably my firewall but I set all that stuff up but nothing... andI can ping the address and surf to it via FireFox. I'd think not being to get to the repositories would be a HUGE issue.](*,)

---

### Post by m42technic on 2006-06-09
Ive been having the same damn problems with my Netgear WGR614 router (using a wired connection).  After plugging the computer directly into the cable modem however, everything works fine!  Do I have Proxy issues?  Networking really isnt my forte.

---

### Post by Muhammad on 2006-06-09
My problem is that I can download everything except linux 686 and nvidia glx.

---

### Post by handy on 2006-06-09
I can't use the repositories either, can't even do a reload?

---

### Post by sixthsiren on 2006-06-09
**Update**

Ok, So I even went as far as going onto my firewall and adding the address security.ubuntu.com and also the ip address 85.133.25.7 in my whitelist. Still nothing...

So I then downloaded and installed Ubuntu 6.06 Desktop version and used Synaptic to try to get some apts and it fails as well... This is seriously getting on my nerves... although I am becoming a master at installing Ubuntu from scratch, maybe I'll write a tutorial. 

Please someone come up with a fix!!![-o<


**** Someone needs to make this a Sticky or something ***

---

### Post by mattwestm on 2006-06-09
[QUOTE=m42technic]Ive been having the same damn problems with my Netgear WGR614 router (using a wired connection).  After plugging the computer directly into the cable modem however, everything works fine!  Do I have Proxy issues?  Networking really isnt my forte.[/QUOTE]

Hmm, that's weird. I have all outgoing ports opened on my firewall. I had absolutely no problems with breezy. As soon as I installed dapper, I start having these problems. I have also tried changing my servers. And still no luck.

---

### Post by sambogosse on 2006-06-09
Hello there !

I had exactly the same problem as you, couldn't download any update with apt.
as referenced in [this topic]("http://www.ubuntuforums.org/showthread.php?t=190679"), i removed the proxy setting in apt.conf and averything is working fine now !! very strange though.

For information I am connected to Internet through a Linsys router/firewall... don't really know if it has anything to do with the config.

Cheers !

---

### Post by mattwestm on 2006-06-09
Congrats!! Removing the proxy line worked!

---

### Post by m42technic on 2006-06-10
[QUOTE=mattwestm]Congrats!! Removing the proxy line worked![/QUOTE]

Ditto! Thanks sambogosse!  :)

---

### Post by handy on 2006-06-10
Did not work for me, but I just looked Networking /  DNS address, & something has changed it back to the router/modem address of 192.168.0.1

I had allready set that to the 2 DNS addresses of my ISP, to make the repo's available last weekend when I installed Dapper!!

So, I think I solved my problem too! :KS

---

