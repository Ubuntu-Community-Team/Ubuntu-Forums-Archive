---
title: "Software Update Problem"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by rialto on 2008-06-30
I am currently running Ubuntu 8.04 Hardy Heron with my Dell Latitude D410 and have run into this one problem 3 times already.  

After a clean install of Hardy Heron, I adjust visual effects in appearance preferences to Extra for my Compiz effects.

Then after i enabled cube, reflection, and scale effects in advanced effects.

Then the software update package comes up and I update EVERYTHING.  This is where the problem comes in.  There's a restart and I go back into Ubuntu to find that everything has changed.  The Theme's shutdown button has changed, the sound icon has changed, the window colors also have changed.  Then when I go back into software update, it comes up with an error message.

I'm not sure how to correct the problem or turn off software update.

Can someone help me?

---

### Post by nowshining on 2008-06-30
>  Then when I go back into software update, it comes up with an error message.
  

what exactly is this error message?

---

### Post by rialto on 2008-06-30
I've reformatted and just installed ubuntu all over again.  I'm also a little skeptical about updating because of the problem, but i'll update and report on the problem.

---

### Post by rialto on 2008-06-30
update: ubuntu just shutoff during it's update at capplets, so i rebooted and tried to update again.

the error message coming from the attempt to update was:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve
'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/main/i18n/Translation-en_US.bz2)  Could not resolve
'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Could not resolve
'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/universe/i18n/Translation-en_US.bz2)  Could not resolve
'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Could not resolve
'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release.gpg)  Could not resolve
'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/main/i18n/Translation-en_US.bz2)  Could not resolve
'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve
'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Tranlation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/i18n/Tranlation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hardy-security/Release.gpg)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Help me out?

---

### Post by rialto on 2008-06-30
Another error also popped up:

E: dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem
E: _cache->open() failed, please report.

---

