---
title: "vpnc on Nokia N800"
date: 2007-09-06
forum: Other OS Talk
---

### Post by thegnome87 on 2007-09-06
Ahh I'm so frustrated.  I'm trying to set up vpnc on my Nokia N800 in order to be able to use my school's wi-fi.

Of course I can just go to the [maemo site]("http://maemo.org/downloads/search/application.html?org_openpsa_products_search%5B1%5D%5Bproperty%5D=description&org_openpsa_products_search%5B1%5D%5Bconstraint%5D=LIKE&org_openpsa_products_search%5B1%5D%5Bvalue%5D=vpnc&org_openpsa_products_search%5B2%5D%5Bproperty%5D=os&org_openpsa_products_search%5B2%5D%5Bconstraint%5D=LIKE&org_openpsa_products_search%5B2%5D%5Bvalue%5D=IT2007&org_openpsa_products_search%5B3%5D%5Bproperty%5D=license&org_openpsa_products_search%5B3%5D%5Bconstraint%5D=LIKE&org_openpsa_products_search%5B3%5D%5Bvalue%5D=&org_openpsa_products_search%5B4%5D%5Bproperty%5D=status&org_openpsa_products_search%5B4%5D%5Bconstraint%5D=LIKE&org_openpsa_products_search%5B4%5D%5Bvalue%5D=&fetch=Fetch%21") and download it but it's circular reason since the whole point of getting the vpn client is so that I can be able to go online in the first place.  

I tried finding a .deb file (download on my laptop then USB the package to tablet) but it won't work either because of dependencies (so you need a repository, which of course needs a net connection).

Is it even possible to install all this xterm, dropbear (to become root), and vpnc without a direct network connection, because my USB approach isn't working.  :(

---

### Post by fistfullofroses on 2007-09-06
Try apt-get --help.
You should have an option to only download the packages and not install (that includes deps). Just make sure you do an "apt-get clean" fist and therefore avoid the confusion of trying to figure out what packages belong to what. Also, "apt-get show vpnc"  will show you a package description and dependency info.

---

### Post by thegnome87 on 2007-09-06
> **fistfullofroses said:**
> Try apt-get --help.
You should have an option to only download the packages and not install (that includes deps). Just make sure you do an "apt-get clean" fist and therefore avoid the confusion of trying to figure out what packages belong to what. Also, "apt-get show vpnc"  will show you a package description and dependency info.

Well I can't type apt-get -- help if the N800 device doesn't even have a terminal installed lol.  Or were you telling me to do this on my laptop and then transfer the files over to the N800?  Would it work, since it is a dif architecture (ARM and not x_86)?

I guess it it unfruitful to install the packages offline.  I'll try to wait until I can get to a free/open hotspot (public library maybe) and try to install vpnc onto the N800 from there.

I'll post again and see what happens and if I can finally get vpnc running on the Nokia tablet.

---

### Post by fistfullofroses on 2007-09-06
Yeah I was going to recommend downloading on your PC and then transferring. I didn't know the n800 was an ARM though. Does it run a debian based system? You may have a serious porting project ahead of you if it doesn't...

---

### Post by thegnome87 on 2007-09-06
> **fistfullofroses said:**
> Yeah I was going to recommend downloading on your PC and then transferring. I didn't know the n800 was an ARM though. Does it run a debian based system? You may have a serious porting project ahead of you if it doesn't...

I think it is an ARM if I'm not mistaken.  And yeah it is a Debian based system.  There are packages, it's just a confusing hassle to try to do it all through my PC  since anytime I transfer the debs it says it can't be installed (the debs are the right arch though).  I'll keep trying.

---

### Post by fistfullofroses on 2007-09-07
well good luck. keep me updated, and post your progress.
I want to get one before too long so it would be nice to know how things proceed.

^.~

---

