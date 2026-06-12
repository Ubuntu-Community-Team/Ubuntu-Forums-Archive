---
title: "&quot;The package X needs to be reinstalled, but I can't find an archive for it.&quot;"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by FrogX on 2012-05-11
Hey!

I dived into the Linux world a few months ago, running Ubuntu 11.10 atm. I am now facing a problem that prevents me from updating my system. 

I recently tried to install openoffice from an archive containing dozens of debs. That apparently didn't go flawlessly. The error I am facing is that I have a package cranking up my Update Manager. 

The error constantly displayed in the upper right corner is:

"(E:The package ooobasis3.4-calc:i386 needs to be reinstalled, but I can't find an archive for it.') This usally means that your installed packages have unmet dependencies."

Why doesn't it find the archive? Tried reinstalling the deb but I get the same error messege.

Would be very, very grateful for some assistance in this matter!

---

### Post by cariboo on 2012-05-11
How did you install OpenOffice? was it from a ppa, or did you just download the .debs from somewhere?

---

### Post by FrogX on 2012-05-11
Downloaded a tar.gz with .debs. 

This one to be exact:
[http://sourceforge.net/projects/openofficeorg.mirror/files/stable/3.4.0/Apache_OpenOffice_incubating_3.4.0_Linux_x86_install-deb_en-US.tar.gz/download](http://sourceforge.net/projects/openofficeorg.mirror/files/stable/3.4.0/Apache_OpenOffice_incubating_3.4.0_Linux_x86_install-deb_en-US.tar.gz/download)

Then I just tried to install all packages using sudo dpkg -i *.deb.

All except the above mentioned package got, seemingly, installed complaint-free.

---

