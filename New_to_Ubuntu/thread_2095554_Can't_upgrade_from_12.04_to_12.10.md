---
title: "Can't upgrade from 12.04 to 12.10"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by F104G on 2012-12-17
currently running 12.04 without any problems.
Decided to upgrade using Update Manager and was told partial upgrade only due to some packages being missing.  I clicked OK but then got this:

[I]Failed to download package files

Check your Internet connection.

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc83_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc83_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns81_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns81_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg82_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg82_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/s/skype/skype_4.1.0.20.0-0ubuntu0.12.04.1_amd64.deb](http://archive.canonical.com/ubuntu/pool/partner/s/skype/skype_4.1.0.20.0-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.150 80]
[/I]
Internet connection is fine.  I clicked OK again, then it asked me if I wanted to continue so I said OK.  Then this:

[I]Could not download the upgrades

The upgrade has aborted. Please check your Internet connection or installation media and try again. All files downloaded so far have been kept.

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.8.dfsg-5.1ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.7.8.dfsg-5.1ubuntu4.2_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_i386.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tiff/libtiff4_3.9.5-2ubuntu1.3_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc83_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisc83_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns81_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libdns81_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg82_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg82_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-80_9.8.1.dfsg.P1-4ubuntu0.4_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.7.8.dfsg-5.1ubuntu4.2_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/s/skype/skype_4.1.0.20.0-0ubuntu0.12.04.1_amd64.deb](http://archive.canonical.com/ubuntu/pool/partner/s/skype/skype_4.1.0.20.0-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.150 80]
Failed to fetch [http://archive.canonical.com/ubuntu/pool/partner/s/skype/skype-bin_4.1.0.20.0-0ubuntu0.12.04.1_i386.deb](http://archive.canonical.com/ubuntu/pool/partner/s/skype/skype-bin_4.1.0.20.0-0ubuntu0.12.04.1_i386.deb) 404  Not Found [IP: 91.189.92.150 80][/I]

Any ideas?

---

### Post by kc1di on 2012-12-17
Sorry you having problems,
perhaps this [page]("http://www.liberiangeek.net/2012/06/upgrade-to-ubuntu-12-10-quantal-quetzal-from-ubuntu-12-04/") may be of help

---

### Post by F104G on 2012-12-17
OK, the only thing different on there is that in settings they show 3 ticks in boxes, whereas I only have the top one ticked.  I changed my settings to match and tried it again but I get the same error messages as before.  :(

---

### Post by squakie on 2012-12-17
Try the following in a terminal:

sudo apt-get update (you may have to try sudo apt-get -f update - a space before the -f)

sudo apt-get upgrade

Then try your upgrade.

---

### Post by kc1di on 2012-12-17
You could try a different server sometimes servers go down.
you can do that by going to the software center >edit>Software Sources
then look in the box that says Download From change that to a different server by clicking on it an choosing one close to you.

Go to a terminal and type ```
sudo apt-get update
```
Then try upgrade manager again.

---

### Post by fdrake on 2012-12-17
> **F104G said:**
> currently running 12.04 without any problems.


May I ask why you want to upgrade from a working ltr version? You will probably just make your life harder...


try squakie advice. The package syou are downloading they do not exist in the repo folder che ck here:

[http://security.ubuntu.com/ubuntu/pool/main/b/bind9/](http://security.ubuntu.com/ubuntu/pool/main/b/bind9/)
 

or try to remove bind and try to reinstall again bind9 package.

---

### Post by F104G on 2012-12-18
> **fdrake said:**
> May I ask why you want to upgrade from a working ltr version?

That's a good question.  I guess I just fancied having the very latest shiny version. :redface:

---

### Post by audiomick on 2012-12-18
> **F104G said:**
> That's a good question.  I guess I just fancied having the very latest shiny version. :redface:

Which is fine. Updating every six months is a bit more work, and may perhaps bring trouble, but usually doesn't.

I have resolved to stay with the last two lts versions on my Desktop, and haven't managed to stick it out yet. Maybe 12.04 will last the distance. No reason for upgrading. I just want to see what the new version looks like. ;)

---

### Post by F104G on 2012-12-20
> **squakie said:**
> (you may have to try sudo apt-get -f update - a space before the -f)

Thanks very much.  I did this and it seemed to do the trick.
Update manager is no longer telling me that I can only do a partial upgrade.

I haven't actually tried the upgrade yet because, taking on-board what fdrake said: if it ain't broke - don't fix it.

Thanks again to everyone who made suggestions ):P

---

