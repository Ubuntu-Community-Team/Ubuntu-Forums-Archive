---
title: "Confused about Synaptic, installing apps manually"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-01
I am confused about the "Synaptic Package Manager" and Apt-Get and installing packages manually.

I am looking to start using an app called [Duplicity]("http://duplicity.nongnu.org/index.html"), the latest release is 0.5.02, yet when I open up the "Synaptic Package Manager" is 0.4.10.

So if I manually install the latest release 0.5.02, what will show up in Synaptic? Will it show that I have the latest version installed? Can I remove/uninstall from synaptic?

[SIZE="1"]Also is there a place to check and see what release versions will be released with the next version of Ubuntu (8.10), so I can see if the new version of Duplicity will be available once 8.10 comes out?[/SIZE]
Edit: scratch that last question I found it: [http://packages.ubuntu.com/intrepid/allpackages](http://packages.ubuntu.com/intrepid/allpackages)
Duplicity 0.4.12 - Why wouldn't they put the latest release in there?

TiA,
-BassKozz

---

### Post by Tatty on 2008-10-01
It depends on how you install it.  If you install it from a .deb or if you compile it using checkinstall instead of make then it will show up in synaptic.  It will not receive any automatic updates as it is not part of a maintained repo, but you will be able to uninstall it simply via synaptic.

I have just had a look at the version on the website.  There are no debs and it appears as though the tarball has its own custom installer, so it looks as though it would not appear in synaptic.  If you chose to install it this way you would have to manually maintain the software yourself.

If you wanted the latest version in the repos you would have to file a bug report to request the package be updated, although as Intrepid is now past feature freeze I am not sure wether this would be accepted.

---

