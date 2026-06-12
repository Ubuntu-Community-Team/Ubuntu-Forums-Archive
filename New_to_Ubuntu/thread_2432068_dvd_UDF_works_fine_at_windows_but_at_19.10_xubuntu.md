---
title: "dvd UDF works fine at windows but at 19.10 xubuntu will not mount."
date: 2019-11-26
forum: New to Ubuntu
---

### Post by dick13d on 2019-11-26
Is it a bug?

UDF cdroms work fine at ubuntu but I am not able to mount UDF DVDRW's. 

dvd's with video works fine and are playing. cdrom works fine with UDF (pictures).

It is no big deal but very very annoying that not all UDF dvd's are readable.

At windows 10 are those DVD's  working fine.

I tried many things like [https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/)

Installed ntfs package because I was not sure it was UDF but windows told me it is UDF.

.....
.....

---

### Post by yetimon_64 on 2019-11-27
> **dick13d said:**
> ...I tried many things like [https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/)

Installed ntfs package because I was not sure it was UDF but windows told me it is UDF.

That link is for playing encrypted dvds and will not have any influence on UDF access. Same with ntfs support, it will not do anything for a UDF disc.

It has been about 8 or 9 years since I tried getting UDF access working on Ubuntu and Windows and at the time I failed badly. If I recall correctly from that time Linux had only limited UDF support and like you note I could only get it fully working on Windows. At the time the version for UDF support for Windows was totally inaccessible on Linux and the disc had to be reformatted each time for Linux use; sounds like it may be still the case. Problem was the Linux formatting was not any good with Windows as well; so I could basically get it to work on one system or the other but could not use the disc between the two systems.

I don't know wether it is that Linux support for UDF is patchy or that Windows is using some proprietory code but it seems UDF cannot be used between the two systems. I don't think it is a bug as such with 19.10 going on my past attempts with UDF and further reading today, but I could be wrong. You should await further advice as my experiments with it were a very very long time ago.

Regards, yeti.

---

