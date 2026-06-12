---
title: "difficulty in getting checkinstall to complete library installations"
date: 2015-02-14
forum: Packaging and Compiling Programs
---

### Post by Nosphky on 2015-02-14
I'm using 1404 and wanting to try out a newer version of gnupg2 than is available in the trusty depositories.  To keep it away from the distro versions (at least initially) I planned on installing in the /usr/local/ file regions.  After reading various Ubuntu Howtos, I decided to use checkinstall rather than 'make install' so as to get a deb package as a by-product and thus make later removal easier.

The first library, libgcrypt-1.6.2, installed ok.  Subsequent libraries ended up with a failure to complete and each time for the same reason. Here is an extract of the logfile from an attempt to install libgpg-error-1.18 :

(Reading database ... 627301 files and directories currently installed.)
Preparing to unpack .../libgpg-error_1.18-1_amd64.deb ...
Unpacking libgpg-error (1.18-1) ...
dpkg: error processing archive /usr/local/src/libgpg-error-1.18/libgpg-error_1.18-1_amd64.deb (--install):
 trying to overwrite '/usr/local/share/info/dir', which is also in package libgcrypt 1.6.2-1
Errors were encountered while processing:
 /usr/local/src/libgpg-error-1.18/libgpg-error_1.18-1_amd64.deb

It seems that checkinstall installed libgcrypt  'dir' and other info files into /usr/local/share/info/ and checkinstall wants to install a file called 'dir' into the same space for each of the other libraries and quits rather than overwrite.

I've seen many references to this link for info on checkinstall :  [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
but nothing on that page seems to help.  

I can see the first library, libgcrypt-1.6.2, in Synaptic Package Manager so I am happy with that  but 
how do I get checkinstall to select a different place for each library's '/info/dir' files ?

---

### Post by Nosphky on 2015-02-15
I seem to have overcome the difficulty by taking the deb package prepared by checkinstall and running :

sudo dpkg -i --force-overwrite libgpg-error_1.18-1_amd64.deb

then I can see the newly installed libgpg-error in Synaptic package manager.

---

