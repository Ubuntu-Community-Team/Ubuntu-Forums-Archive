---
title: "apt-get not working:::&lt;PLZ HELP!!!&gt;"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by shankhs on 2008-05-27
I have just installed ubuntu 7.10 and I was not able to run apt-get update
So I googled and found to include everytime the following:
export http_proxy=http://<username>:<password>@172.16.1.71:8080/
but it is annoying and i want to keep it in a file so that i need not to write this again...
What should i do???
whenever I run apt-get update i get:
root@shanky-desktop:/home/shanky# apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Reading package lists... Done
PLZ help!!!

---

### Post by sayakb on 2008-05-27
Make sure your repositories are enabled (enable it from System->Administration->Software sources -- Enable all Ubuntu software, 3rd party software and Updates)

By any case, are you Sardana?

---

### Post by abn91c on 2008-05-27
> **shankhs said:**
> I have just installed ubuntu 7.10 and I was not able to run apt-get update
So I googled and found to include everytime the following:
export http_proxy=http://<username>:<password>@172.16.1.71:8080/
but it is annoying and i want to keep it in a file so that i need not to write this again...
What should i do???
whenever I run apt-get update i get:
root@shanky-desktop:/home/shanky# apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_IN
Reading package lists... Done
PLZ help!!!

do not use that command, not apt-get command asks for both your username and password. apt-get is pointing to the cdrom, just open the adept manager then manage repositories, under the third party software tab uncheck the reference to the cdrom then click close it will reload the repositories then apt-get shoulde work

---

### Post by shankhs on 2008-05-28
thanx for ur replies let me try it....
btw i m not sardana as asked by linuxisinnovation

---

### Post by shankhs on 2008-05-28
hey abn91c thanx for ur reply...
what is adept manager?
When i tried to update using the update notification icon i got this:

```
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.40.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.40.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.8-7ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.8-7ubuntu3.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-7ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-7ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-7ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-7ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-7ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-7ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libblkid1_1.40.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libblkid1_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.40.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.40.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libuuid1_1.40.2-1ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libuuid1_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.5_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6-0ubuntu2.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6-0ubuntu2.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.7_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.7_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.1-0ubuntu0.7.10.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.1-0ubuntu0.7.10.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu0.7.10.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu0.7.10.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.7_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.12.1-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.12.1-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.12.1-0ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.12.1-0ubuntu1.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.12.1-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.12.1-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.14+2nobinonly-0ubuntu0.7.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.14+2nobinonly-0ubuntu0.7.10_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.14+2nobinonly-0ubuntu0.7.10_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.14+2nobinonly-0ubuntu0.7.10_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.20.0-0ubuntu4.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.20.0-0ubuntu4.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-esd_0.10.6-0ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-esd_0.10.6-0ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libc/libcdio/libcdio6_0.76-1ubuntu2.7.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libc/libcdio/libcdio6_0.76-1ubuntu2.7.10.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac8_1.1.4-3ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/flac/libflac8_1.1.4-3ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/speex/libspeex1_1.1.12-3ubuntu0.7.10.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/speex/libspeex1_1.1.12-3ubuntu0.7.10.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good_0.10.6-0ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good_0.10.6-0ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.6.0+git20071008-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.6.0+git20071008-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/h/hsqldb/libhsqldb-java_1.8.0.8-1ubuntu1.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/h/hsqldb/libhsqldb-java_1.8.0.8-1ubuntu1.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea4_2007-12ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea4_2007-12ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_1.2.4-6ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_1.2.4-6ubuntu6.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-jit_1.2.4-6ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-jit_1.2.4-6ubuntu6.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-common_1.2.4-6ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/mono-common_1.2.4-6ubuntu6.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib1.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib1.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo1.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo1.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_1.2.4-6ubuntu6.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_1.2.4-6ubuntu6.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip2.84-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip2.84-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system1.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system1.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mono/libmono2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-0ubuntu0.7.10.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-0ubuntu0.7.10.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.10.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.10.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6-0ubuntu2.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6-0ubuntu2.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l2_1.10.10-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l2_1.10.10-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l_1.10.10-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l_1.10.10-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-alsa_1.10.10-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-alsa_1.10.10-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-1.10.0_1.10.10-0ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-1.10.0_1.10.10-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.2.1-1ubuntu4.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.2.1-1ubuntu4.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.2.1-1ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.2.1-1ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.3.1-6ubuntu2.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.3.1-6ubuntu2.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp10_5.3.1-6ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp10_5.3.1-6ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.3.0-0ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.3.0-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.30.dfsg-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.30.dfsg-2ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14_2.6.22-14.52_all.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14_2.6.22-14.52_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.3.0-1ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.3.0-1ubuntu5.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.3.0-1ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.3.0-1ubuntu5.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.3.0-1ubuntu5.4_all.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.3.0-1ubuntu5.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.5_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.5_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_0.8.0-1ubuntu0.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_0.8.0-1ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.3_i386.deb)
  407 Proxy Authentication Required
```

what to do ?
I am in a total mess :(

---

### Post by Joeb454 on 2008-05-28
Go to System > Administration > Software Sources

Enter your password

Then choose every option there - **except** Source Code & CD ROM

And in the drop down menu - choose download from "Main Server"

That should let you update again :)

---

### Post by shankhs on 2008-05-28
hey joeb i did that and i got the following error message while I was trying to update:
```
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.6.1-1ubuntu10_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.40.2-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fslibs_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.40.2-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/e2fsprogs_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/findutils/findutils_4.2.31-1ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/findutils/findutils_4.2.31-1ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.8-7ubuntu3.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.8-7ubuntu3.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/db4.4/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/db4.4/libdb4.4_4.4.20-8.1ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-7ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-7ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-7ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-7ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-7ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-7ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ntfs-3g/libntfs-3g16_1.1120-1ubuntu2~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ntfs-3g/libntfs-3g16_1.1120-1ubuntu2~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/ntfs-3g/ntfs-3g_1.1120-1ubuntu2~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/ntfs-3g/ntfs-3g_1.1120-1ubuntu2~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common-data_0.6.20-2ubuntu3.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-common3_0.6.20-2ubuntu3.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-client3_0.6.20-2ubuntu3.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-compat-libdnssd1_0.6.20-2ubuntu3.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.40.2-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcomerr2_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnutls13/libgnutls13_1.6.3-1ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/k/krb5/libkrb53_1.6.dfsg.1-7ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsys2_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libp/libpng/libpng12-0_1.2.15~beta5-2ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/libcupsimage2_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6.4-1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler2_0.6.4-1~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.6.4-1~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.3.1-6ubuntu2.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp-base_5.3.1-6ubuntu2.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl0.9.8_0.9.8e-5ubuntu3.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp10_5.3.1-6ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/libsnmp10_5.3.1-6ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.12+2.7.12-0ubuntu2~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hpijs_2.7.12+2.7.12-0ubuntu2~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/libgs8_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.7_all.deb](http://security.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-common_1.3.2-1ubuntu7.7_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl/openssl_0.9.8e-5ubuntu3.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.1-0ubuntu0.7.10.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssl-blacklist/openssl-blacklist_0.1-0ubuntu0.7.10.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu0.7.10.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/ssl-cert/ssl-cert_1.0.14-0ubuntu0.7.10.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.12-0ubuntu2~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip_2.7.12-0ubuntu2~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.12-0ubuntu2~gutsy1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hplip/hplip-data_2.7.12-0ubuntu2~gutsy1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080229_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en/language-pack-en_7.10+20080229_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_7.10+20080205_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-en-base/language-pack-en-base_7.10+20080205_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080229_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_7.10+20080229_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_7.10+20080205_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en-base/language-pack-gnome-en-base_7.10+20080205_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-image-2.6.22-14-generic_2.6.22-14.52_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.22/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.38_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-ubuntu-modules-2.6.22/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.38_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.5_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-docs/ubuntu-docs_7.10.5_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu14.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt_0.7.6ubuntu14.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libblkid1_1.40.2-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libblkid1_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.40.2-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libss2_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libuuid1_1.40.2-1ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libuuid1_1.40.2-1ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/bzip2_1.0.4-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bzip2/libbz2-1.0_1.0.4-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5_2.5.1-5ubuntu5.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/python2.5/python2.5-minimal_2.5.1-5ubuntu5.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.7.10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2008a-0ubuntu0.7.10_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.6ubuntu14.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apt/apt-utils_0.7.6ubuntu14.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolume-id0_113-0ubuntu17_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolume-id0_113-0ubuntu17_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_113-0ubuntu17_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_113-0ubuntu17_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_113-0ubuntu17_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_113-0ubuntu17_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc32_9.4.1-P1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisc32_9.4.1-P1-3ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns32_9.4.1-P1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libdns32_9.4.1-P1-3ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc30_9.4.1-P1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccc30_9.4.1-P1-3ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg30_9.4.1-P1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libisccfg30_9.4.1-P1-3ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-30_9.4.1-P1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/libbind9-30_9.4.1-P1-3ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres30_9.4.1-P1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/liblwres30_9.4.1-P1-3ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.4.1-P1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/bind9-host_9.4.1-P1-3ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.4.1-P1-3ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bind9/dnsutils_9.4.1-P1-3ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/openssh-client_4.6p1-5ubuntu0.5_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/r/rsync/rsync_2.6.9-5ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.81.3_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager_0.81.3_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.81.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/update-manager/update-manager-core_0.81.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_8.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/app-install-data-commercial/app-install-data-commercial_8.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apturl/apturl_0.1ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apturl/apturl_0.1ubuntu2_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-autoipd_0.6.20-2ubuntu3.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-core5_0.6.20-2ubuntu3.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/avahi-daemon_0.6.20-2ubuntu3.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bittorrent/bittorrent_3.4.2-11ubuntu3~7.10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bittorrent/bittorrent_3.4.2-11ubuntu3~7.10_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/b/bittorrent/python-bittorrent_3.4.2-11ubuntu3~7.10_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/b/bittorrent/python-bittorrent_3.4.2-11ubuntu3~7.10_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/capplets-data_2.20.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/capplets-data_2.20.1-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo2_1.4.10-1ubuntu4.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/libdecoration0_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.18.3-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-common_1.18.3-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.18.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pango1.0/libpango1.0-0_1.18.3-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-common_2.20.1.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-common_2.20.1.1-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-0_2.20.1.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libg/libgnomeui/libgnomeui-0_2.20.1.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-9_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-9_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-10_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-10_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.20.0-0ubuntu7.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/libnautilus-extension1_2.20.0-0ubuntu7.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.20.0-0ubuntu7.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus-data_2.20.0-0ubuntu7.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.20.0-0ubuntu7.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus/nautilus_2.20.0-0ubuntu7.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-esd_0.10.6-0ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-esd_0.10.6-0ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-session/gnome-session_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-session/gnome-session_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.38-0ubuntu4.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/esound/esound-common_0.2.38-0ubuntu4.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/gnome-control-center_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd-alsa0_0.2.38-0ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/esound/libesd-alsa0_0.2.38-0ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/libgnome-menu2_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/libgnome-menu2_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/libpanel-applet2-0_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/gnome-menus_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/gnome-menus_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/python-gmenu_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-menus/python-gmenu_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.20.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-desktop-data_2.20.1-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-window-settings1_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-control-center/libgnome-window-settings1_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.20.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck-common_2.20.1-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck22_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libw/libwnck/libwnck22_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-gnome_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-plugins_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz-core_0.6.2+git20071119-0ubuntu1~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-extra/compiz-fusion-plugins-extra_0.6.0+git20071121-0ubuntu1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/compiz-fusion-plugins-extra/compiz-fusion-plugins-extra_0.6.0+git20071121-0ubuntu1~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.6.2+git20071119-0ubuntu1~gutsy1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/compiz/compiz_0.6.2+git20071119-0ubuntu1~gutsy1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-bsd_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.7_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cupsys/cupsys-client_1.3.2-1ubuntu7.7_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/d/deskbar-applet/deskbar-applet_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/eog/eog_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea4_2007-12ubuntu3.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/texlive-bin/libkpathsea4_2007-12ubuntu3.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler-glib2_0.6.4-1~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/ghostscript/ghostscript-x_8.61.dfsg.1~svn8187-0ubuntu3.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evince/evince_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-13_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_1.12.1-0ubuntu2_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_1.12.1-0ubuntu2_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_1.12.1-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-3_1.12.1-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.14/libgtkhtml3.14-19_3.16.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.14/libgtkhtml3.14-19_3.16.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib0_0.6.5-0ubuntu16.7.10.0_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-glib0_0.6.5-0ubuntu16.7.10.0_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.12.1-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution_2.12.1-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.12.1-0ubuntu1.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-common_2.12.1-0ubuntu1.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.14/gtkhtml3.14_3.16.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtkhtml3.14/gtkhtml3.14_3.16.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.12.1-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/e/evolution/evolution-plugins_2.12.1-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/unzip/unzip_5.52-10ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/file-roller/file-roller_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.14+2nobinonly-0ubuntu0.7.10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_2.0.0.14+2nobinonly-0ubuntu0.7.10_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.14+2nobinonly-0ubuntu0.7.10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_2.0.0.14+2nobinonly-0ubuntu0.7.10_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/foo2zjs/foo2zjs_20070625-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/foo2zjs/foo2zjs_20070625-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gcalctool/gcalctool_5.20.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gcalctool/gcalctool_5.20.2-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-common_2.0.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-common_2.0.1-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-0_2.0.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtksourceview2/libgtksourceview2.0-0_2.0.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.20.3-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit-common_2.20.3-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.20.3-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gedit/gedit_2.20.3-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.4.2-0ubuntu0.7.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/libgimp2.0_2.4.2-0ubuntu0.7.10.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-python_2.4.2-0ubuntu0.7.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-python_2.4.2-0ubuntu0.7.10.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.4.2-0ubuntu0.7.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp_2.4.2-0ubuntu0.7.10.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.4.2-0ubuntu0.7.10.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gimp/gimp-data_2.4.2-0ubuntu0.7.10.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/gnome-about_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.20.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.20.1-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-cards-data_2.20.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-games/gnome-cards-data_2.20.1-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.20.1-0ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel-data_2.20.1-0ubuntu1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-panel/gnome-panel_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.20.0-0ubuntu4.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-screensaver/gnome-screensaver_2.20.0-0ubuntu4.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-0ubuntu0.7.10.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcre3_7.4-0ubuntu0.7.10.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.10.2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pcre3/libpcrecpp0_7.4-0ubuntu0.7.10.2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-monitor/gnome-system-monitor_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-monitor/gnome-system-monitor_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libc/libcdio/libcdio6_0.76-1ubuntu2.7.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libc/libcdio/libcdio6_0.76-1ubuntu2.7.10.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/f/flac/libflac8_1.1.4-3ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/f/flac/libflac8_1.1.4-3ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/speex/libspeex1_1.1.12-3ubuntu0.7.10.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/speex/libspeex1_1.1.12-3ubuntu0.7.10.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_1.0~beta2-2~gutsy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libt/libtheora/libtheora0_1.0~beta2-2~gutsy1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good_0.10.6-0ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gst-plugins-good0.10/gstreamer0.10-plugins-good_0.10.6-0ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gthumb/gthumb_2.10.6-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines_2.12.2-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gtk2-engines/gtk2-engines_2.12.2-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hwdb-client/hwdb-client-common_0.6.11.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hwdb-client/hwdb-client-common_0.6.11.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hwdb-client/hwdb-client-gnome_0.6.11.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hwdb-client/hwdb-client-gnome_0.6.11.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/avahi/libavahi-glib1_0.6.20-2ubuntu3.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/h/hsqldb/libhsqldb-java_1.8.0.8-1ubuntu1.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/h/hsqldb/libhsqldb-java_1.8.0.8-1ubuntu1.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/icu/libicu36_3.6-3ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_1.2.4-6ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-runtime_1.2.4-6ubuntu6.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-gac_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-jit_1.2.4-6ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-jit_1.2.4-6ubuntu6.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-common_1.2.4-6ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/mono-common_1.2.4-6ubuntu6.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib1.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib1.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo1.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-cairo1.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-corlib2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_1.2.4-6ubuntu6.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono0_1.2.4-6ubuntu6.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-security2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-data-tds2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip2.84-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sharpzip2.84-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-data2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-sqlite2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system-web2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system1.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono-system1.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono2.0-cil_1.2.4-6ubuntu6.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/m/mono/libmono2.0-cil_1.2.4-6ubuntu6.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util0_0.6.5-0ubuntu16.7.10.0_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/libnm-util0_0.6.5-0ubuntu16.7.10.0_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l2_1.10.10-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l2_1.10.10-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l_1.10.10-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-v4l_1.10.10-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-alsa_1.10.10-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-plugins-alsa_1.10.10-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-1.10.0_1.10.10-0ubuntu2.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pwlib/libpt-1.10.0_1.10.10-0ubuntu2.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.2.1-1ubuntu4.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin-data_2.2.1-1ubuntu4.1_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.2.1-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.2.1-1ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.3.0-0ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxfont/libxfont1_1.3.0-0ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.30.dfsg-2ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/libxml2-utils_2.6.30.dfsg-2ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14_2.6.22-14.52_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14_2.6.22-14.52_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.22/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-common_2.6.22.4-14.10_all.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-common_2.6.22.4-14.10_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-2.6.22-14-generic_2.6.22.4-14.10_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.22/linux-restricted-modules-2.6.22-14-generic_2.6.22.4-14.10_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.5-0ubuntu16.7.10.0_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.6.5-0ubuntu16.7.10.0_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.5-0ubuntu11~7.10.0_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.6.5-0ubuntu11~7.10.0_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-impress_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-draw_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.3.0-1ubuntu5.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-human_2.3.0-1ubuntu5.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-common_2.3.0-1ubuntu5.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.3.0-1ubuntu5.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.3.0-1ubuntu5.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.3.0-1ubuntu5.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/ttf-opensymbol_2.3.0-1ubuntu5.4_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5.4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-core_2.3.0-1ubuntu5.4_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/p/pidgin/pidgin_2.2.1-1ubuntu4.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libx/libxml2/python-libxml2_2.6.30.dfsg-2ubuntu1.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/sound-juicer/sound-juicer_2.20.1-0ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/sound-juicer/sound-juicer_2.20.1-0ubuntu1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.5_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/o/openssh/ssh-askpass-gnome_4.6p1-5ubuntu0.5_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_0.8.0-1ubuntu0.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tomboy/tomboy_0.8.0-1ubuntu0.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.4~beta1-0ubuntu6_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/ubufox/ubufox_0.4~beta1-0ubuntu6_all.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.3.0.0.dfsg-12ubuntu8.3_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.1.1-0ubuntu9.1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-intel/xserver-xorg-video-intel_2.1.1-0ubuntu9.1_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.20.0-0ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gnome-system-tools/gnome-system-tools_2.20.0-0ubuntu2_i386.deb)
  407 Proxy Authentication Required


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.3_i386.deb)
  407 Proxy Authentication Required
```

itz the same thing :(
I AM HAVING A HARD TIME WITH UBUNTU 7.10 :(

---

### Post by quinnten83 on 2008-05-28
How are you connected to the internet?
It says that you are behind a proxy, and you need to set it up first before Ubuntu can connect to the internet to download the packages it needs. Are you installing on a computer at home behind a router or are you installing somewhere else, like an office?

---

### Post by shankhs on 2008-05-28
yes i am behind proxy in my college...

---

### Post by Joeb454 on 2008-05-28
That could be your problem then, is there any chance you can try this at home and let us know if the problem still exists?

Also next time could you use the [ CODE][ /CODE] tags around the output? :) It makes it easier to read

*Note that you do not need the spaces as I used above

---

### Post by shankhs on 2008-05-28
thanx for the advice...
but i live in hostel of the college:
 i tried to google a lot and i found that i have to write :
```
export http_proxy=http://<username>:<password>@172.16.1.71:8080/
```
but i dont know in which file!!!! and where???
and also here is my cat /etc/apt/sources.list
```

shanky@shanky-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports universe main multiverse restricted
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by Joeb454 on 2008-05-28
Do you have to sign into the proxy or anything before you are permitted to use the internet?

You could also speak to the network admin to see what they can do :)

---

### Post by shankhs on 2008-05-28
ya i do have to sign into proxy before i am able to use the internet...

---

### Post by Joeb454 on 2008-05-28
Sign into that and then try updating/upgrading

---

### Post by shankhs on 2008-05-28
MAN you havent understand my problem or you must be joking...
i am trying to do with this in the shell and asking ways so that i can upgrade the os..
you have upgraded your OS earlier right?
OK then, you aint behind proxy but I am.
i dont know if there is any way that ubuntu terminal, pops out a window asking for username and passwd once you enter sudo apt-get upgrade...
do u know?
if u do plz tell me i am waiting for that!!!
if u dont i googled and found that we have to write username and proxy in some file i dont know where?
and i am looking for this---!!!!
I hope I am clear this time!!!!

---

### Post by quinnten83 on 2008-05-28
> **shankhs said:**
> MAN you havent understand my problem or you must be joking...
i am trying to do with this in the shell and asking ways so that i can upgrade the os..
you have upgraded your OS earlier right?
OK then, you aint behind proxy but I am.
i dont know if there is any way that ubuntu terminal, pops out a window asking for username and passwd once you enter sudo apt-get upgrade...
do u know?
if u do plz tell me i am waiting for that!!!
if u dont i googled and found that we have to write username and proxy in some file i dont know where?
and i am looking for this---!!!!
I hope I am clear this time!!!!

Well, i think I know what might solve the problem, but please do not be snippy with people who are trying to help, it is very rude, and that is frowned up on around here.

try the following
you will need to know the proxy address for your campus. You might have to ask an administrator for that:
- go to System>Preferences>network Proxy
- select the "manual proxy configuration" option and fill in the details

after that you should be able to access the internet and also download packages.

---

### Post by shankhs on 2008-05-28
SORRY if i have hurt anybody's sentiments but itz really frustrating i am a newbie i got annoyed by vista and so switched to ubuntu and now i am getting more annoyance becuse my os is not updating...
so quinnten83 dats gonna fix the problem thanx.

---

### Post by shankhs on 2008-05-28
hey i did that and when i ran i got this:
E: Type '<LINK' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
now i am confused again what to do?

---

### Post by PmDematagoda on 2008-05-28
Post the output of:-
```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by shankhs on 2008-05-28
i got 
```

                <tr valign='top'>
                <td  align=center class="announce" >
                <font size=1pts>Dated 2008-04-08<br>for B.Tech. students of engineering colleges<br>Expiry 2008-07-08</td>
                </tr></table>
               </td></tr></table>
                <table  border=0 cellpadding=0 cellspacing=4>
                <tr valign='top'>
                <td><img src='images/arrow.gif'></td>
                <td onmouseover="show('announce8')" onmouseout="hide('announce8')"  >
                <a href="http://www.iiita.ac.in/summerschools/">Summer Schools 2008</a><br/>
                <table class="announce" id="announce8" border=0 cellpadding=0 cellspacing=5>
                <tr valign='top'>
                <td  align=center class="announce" >
                <font size=1pts>Dated 2008-03-07<br>Information Security, Robotics & Embedded Systems, Management of RnD Projects, Next Generation Wireless Networks<br>Expiry 2008-05-07</td>
                </tr></table>
               </td></tr></table><div align='right'><a href='http://www.adobe.com/products/acrobat/readstep2.html'>Download&nbsp;PDF&nbsp;Reader</a>&nbsp;|&nbsp;<a href='inner.php?conf=annmore'>More&nbsp;Announcements...</a></div>  </div>

        <div id="left">
                <div id ="leftcorner">
                                <form name=frmsearch action='inner.php?conf=search' method=POST>
                <table class="search" cellspacing=2 cellpadding=2 border=0>
                <tr>
                        <td>Search the site</td>
                </tr>
                <tr>
                        <td><input name='q' class='searchtext' type='text' /></td>
                        <td width=0></td>
                        <td><input type='submit' value='Search' name='B1' class='btn' /></td>
                </tr>
                </table>
        </form>
                        </div>
                <div id ="menu">
                <LINK rel='stylesheet' type='text/css' name='iiita'  href='style_green.css'>
        <table width=170 border=0 cellpadding=0 cellspacing=0>
                <tr>
                        <td width=175 height=25px onmouseover="style.backgroundColor='#FFEBCD';"
                        onmouseout="style.background='url(images/transparent.gif)';">
                        &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<a href="index.php"><b>HOME</b></a>
                        <br/>

                        </td>
                </tr>
                <tr>
                        <td height=25px onmouseover="style.backgroundColor='#FFEBCD';show('About Us')";
                        onmouseout="style.background='url(images/transparent.gif)';hide('About Us')"  >
                        <a href="#nogo"><b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;The Institute</b></a><br/>
                                <table bgcolor=#FFEBCD width=150 class="menu" id="About Us" border=0 cellpadding=0 cellspacing=0>
                                        <tr>
                                                <td height=20 class="menu"  onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'" >
                                                <a href="inner.php?conf=abti">About Us</td>
                                        </tr>

                                        <tr>
                                                <td height=20 class="menu"onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="inner.php?conf=camp">Campus</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href='gallery.php' target='_blank'>IIITA in Photos</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="inner.php?conf=facil">Facilities</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="inner.php?conf=dirmsg">Director's Message</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';"
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="inner.php?conf=ranking">IIITA Ranking</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';"
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="inner.php?conf=reach">Reaching IIITA</td>
                                        </tr>
                                </table>
                        </td>
                </tr>

                <tr>
                        <td height=25px onmouseover="style.backgroundColor='#FFEBCD';show('Administration')" 
                        onmouseout="style.background='url(images/transparent.gif)';hide('Administration')">
                        <a href="#nogo"><b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Administration</b></a><br/>
                                <table bgcolor=#FFEBCD class="menu" id="Administration" width=180px border=0 cellpadding=0 cellspacing=0>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="inner.php?conf=admin">Overview</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="inner.php?conf=bog">Board of Governors</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="inner.php?conf=senate">Senate</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="inner.php?conf=fina">Finance Committee</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="inner.php?conf=builcomm">Building & Works Committee</td>

                                        <!--</tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="#">Officers</td>
                                        </tr>-->
                                </table>
                        </td>
                </tr>

                <tr>
                        <td height=25px onmouseover="style.backgroundColor='#FFEBCD';show('Academics')" 
                        onmouseout="style.background='url(images/transparent.gif)';hide('Academics')"><b>
                        <a href="#nogo">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Academics</b></a><br/>
                                <table bgcolor=#FFEBCD class="menu" id="Academics"width=180px border=0 cellpadding=0 cellspacing=0>
                                        <tr >
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="inner.php?conf=ugrad">Undergraduate Programme</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="inner.php?conf=grad">Graduate Programme</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="inner.php?conf=phd">Doctoral Programme</td>
                                        </tr>
                                        </tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="inner.php?conf=deanmsg">Dean's Message</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="inner.php?conf=fac">Faculty Profiles</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="pub/brochure05.pdf">Prospectus (PDF)</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="pub/academic-calendar2007.pdf">Academic Calender (PDF)</td>
                                        </tr>
                                </table>
                        </td>
                </tr>
                <tr>
                        <td height=25px  onmouseover="style.backgroundColor='#FFEBCD';show('students')"
                        onmouseout="style.background='url(images/transparent.gif)';hide('students')"><b>
                        <a href="#nogo">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Students</b></a><br/>
                                <table bgcolor=#FFEBCD class="menu" id="students"width=140px border=0 cellpadding=0 cellspacing=0>
                                        <tr>
                                        <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="inner.php?conf=geninfo">Freshers Guide</td>
                                        </tr>
                                        <tr>
                                        <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="inner.php?conf=studprof">Brief Profiles</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="inner.php?conf=camp&hilite=hostels">Hostel Life</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="inner.php?conf=clubs">Club Activities</td>
                                        </tr>
                                        <tr>
                                           <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';"
                             onmouseout="style.backgroundColor='#FFEBCD'">
                                                 <a href="http://alumni.iiita.ac.in">Alumni Association</td>
                                        </tr>
                                </table>
                        </td>
                </tr>

                <tr>
                        <td height=25px onmouseover="style.backgroundColor='#FFEBCD';show('research')";
                        onmouseout="style.background='url(images/transparent.gif)';hide('research')"  >
                        <a href="#nogo"><b>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Research</b></a><br/>
                                <table width=250 bgcolor=#FFEBCD class="menu" id="research" border=0 cellpadding=0 cellspacing=0>
                                        <tr>
                                                <td height=20 class="menu"  onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'" >
                                                <a href="#">MHRD Projects</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="http://ircb.iiita.ac.in">Indo Russian Center for Biotechnology</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu"onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="http://udl.iiita.ac.in">Universal Digital Library</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="http://robita.iiita.ac.in">Robotics</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="inner.php?conf=proj">Student's Projects</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="http://seh.iiita.ac.in">Software Engineering Helpdesk</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="http://researchnet.iiita.ac.in">IIITA ResearchNet</a></td>
                                        </tr>
                                </table>
                        </td>
                </tr>

                <tr>
                        <td height=25px  onmouseover="style.backgroundColor='#FFEBCD';show('library')" 
                        onmouseout="style.background='url(images/transparent.gif)';hide('library')"><b>
                        <a href="#nogo">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Library</b></a><br/>
                                <table bgcolor=#FFEBCD width=150px class="menu" id="library" border=0 cellpadding=0 cellspacing=0>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> 
                                                <a href="http://library.iiita.ac.in"target="_blank">Central&nbsp;Library&nbsp;(OPAC)</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="http://udl.iiita.ac.in" target="_blank">Universal&nbsp;Digital&nbsp;Library</td>
                                        </tr>
            <tr>
                 <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                                onmouseout="style.backgroundColor='#FFEBCD'"> <a href="http://paniit.iitd.ac.in/indest/eres.php?memID=9"
                                target="_blank">INDEST&nbsp;Consortium</td>
            </tr>
                                </table>
                        </td>
                </tr>
<!--
                <tr>
                        <td  height=25px onmouseover="style.backgroundColor='#FFEBCD';show('placements')"
                        onmouseout="style.background='url(images/transparent.gif)';hide('placements')"><b>
                        <a href="#nogo">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Placements</b></a><img src='media/blink.gif'></img><br/>
                                <table bgcolor=#FFEBCD class="menu" id="placements"width=140px border=0 cellpadding=0 cellspacing=0>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'">
                                                <a href="http://placement.iiita.ac.in">BTech/MTech</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="http://mba.iiita.ac.in/placement">MBA</td>
                                        </tr>
                                        <tr>
                                                <td height=20 class="menu" onmouseover="style.backgroundColor='#cee2a7';" 
                           onmouseout="style.backgroundColor='#FFEBCD'"> <a href="http://ms.iiita.ac.in/index3.html">MS</td>
                                        </tr>
                                </table>
                        </td>
                </tr>
-->
        </table>                </div>
                <div id="link_above_login_box">
                <table border=0 cellspacing=4 cellpadding=0>
                        <tr>
                                <td>&nbsp;&nbsp;<a href='http://mail.iiita.ac.in'>&nbsp;<b>Mailbox@IIITA</b></a></td>
                        </tr>
                        <tr>
                                <td>&nbsp;&nbsp;<a href='http://forum.iiita.ac.in'>&nbsp;<b>Student Forum</b></a></td>
                        </tr>
                        <tr>
                                <td>&nbsp;&nbsp;<a href='gallery.php' target='_blank'>&nbsp;<b>Photo Gallery</b></a></td>
                        </tr>
                        <tr>
                                <td>&nbsp;&nbsp;<a href='inner.php?conf=phone'>&nbsp;<b>Telephones</b></a></td>
                        </tr>
                </table>
                                </div>
                <div id="search_people">
                                <form action='inner.php?conf=pplsearch&mode=search' method=POST>
                <table class="search" cellspacing=2 cellpadding=0 border=0>
                <tr>
                        <td>Search the people</td>
                </tr>
                <tr>
                        <td><input name='txtName' class='searchtext' type='text' /></td>
                        <td width=0></td>
                        <td><input type='submit' value='Search' name='B1' class='btn' /></td>
                </tr>
                </table>
        </form>
                        </div>

                <div id='myiiita_btn' onMouseover='show_login_hover();' onMouseout='hide_login_hover();'        onClick='show_login();'></div>
                <div id="login_box">
                                <form name="frmLogin" id='login' action='inner.php' method=post>
                <table width=100px class="login_box" border=0 cellpadding=0 cellspacing=2>
                        <tr>
                                <td></td>
                                <td height=20 align=right>
                                        <input type="button" class="btn_close" value="X" onclick="hide_login();">
                                        <input type=hidden name=login>
                                        <!--helps inner.php know that we are trying to logon, so that it can create a session-->
                                        <input type=hidden name=target value=''>
                                </td>
                        </tr>
                        <tr>
                                <td><b>Username</b></td>
                                <td height=15><input class='text' type='text' name='txtID'></td>
                        </tr>
                        <tr>
                                <td height=15><b>Password</b></td>
                                <td><input class='text' type='password' name='txtPWD'></td>
                        </tr>
                        <tr>
                                <td height=30><input type='submit' class='btn_login' value='Login'></td>
                        </tr>
                </table>
                </form>
                </div>
        </div>

        <div id="footer">

                <a href='inner.php?conf=contact'>Contact </a>
                | <a href='inner.php?conf=indem'>INDEM [IIITA Network Development, Engineering & Management]</a>
                | <a href='inner.php?conf=webgrp'>Website Team</a>
                | <a href='http://hindi.iiita.ac.in/'>Hindi Version</a>
                <br>Website Best viewed at 1024x768 resolution.
                        </div>
</div>
<!--
<script src="http://www.google-analytics.com/urchin.js" type="text/javascript">
</script>
<script type="text/javascript">
_uacct = "UA-2858744-1";
urchinTracker();
</script>
-->
</body>
</html>

```

---

### Post by PmDematagoda on 2008-05-28
Are you sure that your path is right? Because all I got was:-
```
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
# deb-src http://packages.medibuntu.org/ hardy free non-free

```
Which means that you are looking at the wrong file.

---

### Post by shankhs on 2008-05-28
hey believe me i just copy pasted your command
```

cat /etc/apt/sources.list.d/medibuntu.list

```
moreover i tried 
```

gedit /etc/apt/sources.list.d/medibuntu.list

```
i got the same thing(which is obvious)
how can i uninstall medibuntu i am a newbie and i am lost :(

---

### Post by PmDematagoda on 2008-05-28
Then just remove it with:-
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```
and do:-
```
sudo apt-get update
```

---

### Post by shankhs on 2008-05-28
sir what is the problem when i ran
```

sudo apt-get update

```
i got this:
```

shanky@shanky-desktop:/$ sudo apt-get update
Ign http://archive.canonical.com gutsy Release.gpg
Ign http://archive.canonical.com gutsy/partner Translation-en_IN
Ign http://security.ubuntu.com gutsy-security Release.gpg
Ign http://security.ubuntu.com gutsy-security/universe Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/main Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/multiverse Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/restricted Translation-en_IN
Ign http://archive.canonical.com gutsy Release 
Ign http://archive.ubuntu.com gutsy Release.gpg
Ign http://security.ubuntu.com gutsy-security Release
Ign http://archive.ubuntu.com gutsy/main Translation-en_IN
Ign http://archive.ubuntu.com gutsy/universe Translation-en_IN
Ign http://archive.ubuntu.com gutsy/restricted Translation-en_IN
Ign http://archive.ubuntu.com gutsy/multiverse Translation-en_IN
Ign http://archive.ubuntu.com gutsy-updates Release.gpg
Ign http://archive.ubuntu.com gutsy-updates/universe Translation-en_IN
Ign http://archive.ubuntu.com gutsy-updates/main Translation-en_IN
Ign http://archive.canonical.com gutsy/partner Packages
Ign http://archive.ubuntu.com gutsy-updates/multiverse Translation-en_IN
Ign http://archive.ubuntu.com gutsy-updates/restricted Translation-en_IN
Ign http://archive.canonical.com gutsy/partner Sources               
Ign http://security.ubuntu.com gutsy-security/universe Packages      
Err http://archive.canonical.com gutsy/partner Packages
  302 Found
Ign http://archive.ubuntu.com gutsy-proposed Release.gpg
Ign http://archive.ubuntu.com gutsy-proposed/universe Translation-en_IN
Ign http://archive.ubuntu.com gutsy-proposed/main Translation-en_IN
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Translation-en_IN
Ign http://archive.ubuntu.com gutsy-proposed/restricted Translation-en_IN
Ign http://security.ubuntu.com gutsy-security/main Packages
Ign http://security.ubuntu.com gutsy-security/multiverse Packages
Ign http://security.ubuntu.com gutsy-security/restricted Packages
Ign http://archive.ubuntu.com gutsy-backports Release.gpg
Ign http://archive.ubuntu.com gutsy-backports/universe Translation-en_IN
Ign http://archive.ubuntu.com gutsy-backports/main Translation-en_IN
Ign http://archive.ubuntu.com gutsy-backports/multiverse Translation-en_IN
Err http://security.ubuntu.com gutsy-security/universe Packages
  302 Found
Err http://security.ubuntu.com gutsy-security/main Packages
  302 Found
Err http://security.ubuntu.com gutsy-security/multiverse Packages
  302 Found
Ign http://archive.ubuntu.com gutsy-backports/restricted Translation-en_IN
Err http://archive.canonical.com gutsy/partner Sources
  302 Found
Ign http://archive.ubuntu.com gutsy Release    
Ign http://archive.ubuntu.com gutsy-updates Release
Ign http://archive.ubuntu.com gutsy-proposed Release
Ign http://archive.ubuntu.com gutsy-backports Release
Ign http://archive.ubuntu.com gutsy/main Packages
Ign http://archive.ubuntu.com gutsy/universe Packages
Ign http://archive.ubuntu.com gutsy/restricted Packages
Ign http://archive.ubuntu.com gutsy/multiverse Packages
Ign http://archive.ubuntu.com gutsy-updates/universe Packages
Ign http://archive.ubuntu.com gutsy-updates/main Packages
Ign http://archive.ubuntu.com gutsy-updates/multiverse Packages
Ign http://archive.ubuntu.com gutsy-updates/restricted Packages
Err http://security.ubuntu.com gutsy-security/restricted Packages
  302 Found
Ign http://archive.ubuntu.com gutsy-proposed/universe Packages
Ign http://archive.ubuntu.com gutsy-proposed/main Packages
Ign http://archive.ubuntu.com gutsy-proposed/multiverse Packages
Ign http://archive.ubuntu.com gutsy-proposed/restricted Packages
Ign http://archive.ubuntu.com gutsy-backports/universe Packages
Ign http://archive.ubuntu.com gutsy-backports/main Packages
Ign http://archive.ubuntu.com gutsy-backports/multiverse Packages
Ign http://archive.ubuntu.com gutsy-backports/restricted Packages
Err http://archive.ubuntu.com gutsy/main Packages
  302 Found
Err http://archive.ubuntu.com gutsy/universe Packages
  302 Found
Err http://archive.ubuntu.com gutsy/restricted Packages
  302 Found
Err http://archive.ubuntu.com gutsy/multiverse Packages
  302 Found
Err http://archive.ubuntu.com gutsy-updates/universe Packages
  302 Found
Err http://archive.ubuntu.com gutsy-updates/main Packages
  302 Found
Err http://archive.ubuntu.com gutsy-updates/multiverse Packages
  302 Found
Err http://archive.ubuntu.com gutsy-updates/restricted Packages
  302 Found
Err http://archive.ubuntu.com gutsy-proposed/universe Packages
  302 Found
Err http://archive.ubuntu.com gutsy-proposed/main Packages
  302 Found
Err http://archive.ubuntu.com gutsy-proposed/multiverse Packages
  302 Found
Err http://archive.ubuntu.com gutsy-proposed/restricted Packages
  302 Found
Err http://archive.ubuntu.com gutsy-backports/universe Packages
  302 Found
Err http://archive.ubuntu.com gutsy-backports/main Packages
  302 Found
Err http://archive.ubuntu.com gutsy-backports/multiverse Packages
  302 Found
Err http://archive.ubuntu.com gutsy-backports/restricted Packages
  302 Found
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz  302 Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz  302 Found
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz  302 Found
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by fickenbaisage on 2008-05-28
Maybe you could try to change where you download your sources from. Go to System -> Administration -> Software Sources, under the first tab there's "download from", click on the website and a drop down box will appear. Select Other and a new window will appear, press select best server.

---

### Post by shankhs on 2008-05-28
hey i tried that i got these error:
```

http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz: 407 Proxy Authentication Required
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required

```
????????What proxy ????
i tried main server and many other server still getting such type of responses...
I have setup proxy in system->preferences->network proxy and itz all fine..???

---

### Post by fickenbaisage on 2008-05-28
> **shankhs said:**
> hey i tried that i got these error:
```

http://security.ubuntu.com/ubuntu/dists/gutsy-security/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://security.ubuntu.com/ubuntu/dists/gutsy-security/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://archive.canonical.com/ubuntu/dists/gutsy/partner/source/Sources.gz: 407 Proxy Authentication Required
http://security.ubuntu.com/ubuntu/dists/gutsy-security/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://security.ubuntu.com/ubuntu/dists/gutsy-security/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-updates/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-updates/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-updates/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-updates/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-proposed/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-proposed/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-proposed/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-proposed/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-backports/universe/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-backports/main/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-backports/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required
http://ftp.iitm.ac.in/ubuntu/dists/gutsy-backports/restricted/binary-i386/Packages.gz: 407 Proxy Authentication Required

```
????????What proxy ????
i tried main server and many other server still getting such type of responses...
I have setup proxy in system->preferences->network proxy and itz all fine..???

When you are configuring network proxy preferences under "system -> preferences -> network proxy preferences", did you select the button "use the same proxy for all protocols"?

---

### Post by shankhs on 2008-05-28
thanx for all you frnds out there really got frustrated but now i am happy and gonna enjoy gusty
thanx again for all the help and time u gave to me...:)

---

### Post by fickenbaisage on 2008-05-28
> **shankhs said:**
> thanx for all you frnds out there really got frustrated but now i am happy and gonna enjoy gusty
thanx again for all the help and time u gave to me...:)

I'm sorry I couldn't help you :(

---

### Post by shankhs on 2008-05-28
hey no i just figured out what was wrong....
so just THANK YOU
hey i just want to thanks all
can you tell me how to do this???
:):):)
;););)

---

### Post by bapoumba on 2008-05-28
> **shankhs said:**
> hey no i just figured out what was wrong....
so just THANK YOU
hey i just want to thanks all
can you tell me how to do this???

There are two things you can do:
- post the way you solved your issue (it can be helpful to others)
- use the little blue ribbon button bottom right to each post that was helpful. It will add a "thank you" to the user :)

---

### Post by shankhs on 2008-05-28
as i adviced by bapounba to tell how i solved the issue:
1.I was unable to sudo apt-get upgrade (i had posted everything sources.list and what was coming after running the command)
2.My comp is behind a proxy so I must set the username and password somewhere...
3.then after gruelling 8 hours I found that go to system->preferences->network proxy and put in the proxy that your net admin has given to you check the button that says apply to all
There is a small button on the right that says DETAILS click on that put your username and proxy and enjoy the power of apt-get....
I hope this might be helpful to somebody.;):)

---

