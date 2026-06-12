---
title: "dpkg-buildpackage sign using pgp"
date: 2006-10-13
forum: Programming Talk
---

### Post by cytoplasm on 2006-10-13
I followed the instructions from the 'Debian New Maintainer's Guide' on creating a .deb package but I'm having issues with signing. The Guide mentions that I would be prompted twice for my passphrase. I do not get prompted. Here is an example:

$ dpkg-buildpackage -rfakeroot
<snip>
dpkg-deb: building package `foo' in `../foo_1.0.4-2_i386.deb'.
 signfile foo_1.0.4-2.dsc
gpg: skipped "First Last <first.last@company.com>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

Since I'm using PGP Command Line 9.0.4 instead of gpg this is somewhat understandable. So I changed my command to the following:

$ dpkg-buildpackage -rfakeroot  -k"First Last" -ppgp
<snip>
dpkg-deb: building package `foo' in `../foo_1.0.4-2_i386.deb'.
 signfile foo_1.0.4-2.dsc
0xCAFB4D07:sign (3011:invalid passphrase specified)

It accurately detected the key ID from my PGP key ring but I am not prompted for the passphrase. I've searched the web to no avail and am hoping some of you experts can offer some advice.

I've also used the '-uc -us' flag and then ran 'debsign' but that complained about the passphrase too.

Much appreciated.

---

