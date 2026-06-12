---
title: "PPA sources not updating 404 error"
date: 2012-02-28
forum: New to Ubuntu
---

### Post by HomesteadMommy on 2012-02-28
I'm having trouble when I try to check for updates in Ubuntu 11.10.  The updates will install but when you click check to update the package info I keep getting this error.  Isn't this the main ppa for Ubuntu??  I haven't changed it so I don't know why it's sending an error.  Is their site having trouble or have the ppa links changed?


W:Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks!

---

### Post by matt_symes on 2012-02-28
Hi

If you click on this link

[http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/)

you will see there is no repository for Oneiric for Cybolic.

You may as well remove it.

Kind regards

---

### Post by plucky on 2012-02-28
> **HomesteadMommy said:**
> I'm having trouble when I try to check for updates in Ubuntu 11.10.  The updates will install but when you click check to update the package info I keep getting this error.  Isn't this the main ppa for Ubuntu??  I haven't changed it so I don't know why it's sending an error.  Is their site having trouble or have the ppa links changed?


W:Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

Thanks!

PPA's are for adding upgraded software to Ubuntu and are maintained independently from the main repositories.

Your PPA doesn't have a version for Oneiric,which is why you are getting the 404 errors.

See [Here](http://ppa.launchpad.net/cybolic/ppa/ubuntu/dists/)

Open Software Sources and disable that PPA as a Source.Do the same for any more that do not have a repository for Oneiric.

Good Luck

---

### Post by HomesteadMommy on 2012-02-28
Thank you!  I deleted it, I didn't remember adding it in there so I thought it might have been part of the Ubuntu main updates. :tongue:

---

