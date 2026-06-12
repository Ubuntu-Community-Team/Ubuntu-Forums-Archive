---
title: "perl Audio::CD module in repo newer than CPAN"
date: 2006-02-26
forum: Programming Talk
---

### Post by PMO6022 on 2006-02-26
I've just noticed something very interesting and I'm hoping someone can shed some light on this...

The version of the perl Audio::CD module available on CPAN is version 0.04 _[http://search.cpan.org/~dougm/Audio-CD-0.04/CD.pm]("http://search.cpan.org/%7Edougm/Audio-CD-0.04/CD.pm")_ while the version available in the debian or ubuntu repos is version 0.05 - [http://packages.ubuntu.com/breezy/perl/libaudio-cd-perl]("http://packages.ubuntu.com/breezy/perl/libaudio-cd-perl")  

This is kind of messing me up, because it makes any programs I write relying on the ubuntu/debian version of the module inherently less portable.  If I use functions only available in the 0.05 version of the module, then only people using debian or debian derived distros can use my script.

Is it possible to unpack the .deb and compile the module by hand so as to make it more portable?  Is the 0.05 version available for download in any other format?

Thanks.

---

