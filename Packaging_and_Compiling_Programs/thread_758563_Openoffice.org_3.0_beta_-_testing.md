---
title: "Openoffice.org 3.0 beta - testing"
date: 2008-04-18
forum: Packaging and Compiling Programs
---

### Post by steffen on 2008-04-18
Has anyone had success in testing OpenoOffice.org 3.0 testing on Ubuntu, without messing up the 2.4 version in Ubuntu?

There is a Debian package available here: [http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/DEV300/](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/DEV300/) but it seems to install over OpenOffice.org 2.4.

---

### Post by calc on 2008-04-18
I will be uploading debs to Intrepid probably in about a month or so.

---

### Post by meborc on 2008-04-18
hey, i have the same problem... meaning i would really like to try out 3.0 beta, but when installing the beta debs, i seem not to be able to launch it :) 

[http://www.oooninja.com/2008/04/openofficeorg-30-beta.html](http://www.oooninja.com/2008/04/openofficeorg-30-beta.html)

---

### Post by Andrew.Z on 2008-04-19
What problem do you have?  Is there an error message?  If so, post it verbatim. 


Have you tried from the command line something like this?
```

/opt/ooo-dev3.0/program/soffice

```

---

### Post by steffen on 2008-04-24
Meborc,

When you installed OOo3, did it overwrite your OOo2?

---

### Post by micha137 on 2008-04-24
Hi there,

I am also having trouble installing OODEV300 m10 (on ubuntu Gutsy).
version m5  and m7 could be installed and run on my system(m7 crashed on opening the base component though) but m9 and m10 threw plenty of error messages on me on attempts to install and couldn't be launched of course.
After uninstalling the Ubuntu-verwsion of Openoffice(2.3.0), the installation procedure of m10 went through and I found soffice in /opt/ooo-dev3/program/


Is there any way for parallel use without the dirty solution of hiding a "secret" copy of the stable version of Openoffice on the disk?

regards
   micha137

---

### Post by Andrew.Z on 2008-04-24
This was recently discussed elsewhere

"Installing OOo 2.4.0 and DEV300m5 in parallel on Ubuntu"
[http://www.openoffice.org/servlets/BrowseList?list=dev&by=thread&from=1985109](http://www.openoffice.org/servlets/BrowseList?list=dev&by=thread&from=1985109)

---

### Post by FSHero on 2008-05-07
A direct link to some good instructions:
[http://wiki.services.openoffice.org/wiki/Run_OOo_versions_parallel](http://wiki.services.openoffice.org/wiki/Run_OOo_versions_parallel)

It is a shame however that there isn't just a single zip file you can extract everything from. I imagine that Windows got a nice self-installing wizard... why did they make it so complicated to use debs?

Luckily I'm comfortable using the command line. But I'm not sure all other Ubuntu users are...

BTW, OpenOffice.org 3 beta is looking good from the very brief try I've had of it!!

---

### Post by steffen on 2008-05-09
> **FSHero said:**
> A direct link to some good instructions:
[http://wiki.services.openoffice.org/wiki/Run_OOo_versions_parallel](http://wiki.services.openoffice.org/wiki/Run_OOo_versions_parallel)

[...]

BTW, OpenOffice.org 3 beta is looking good from the very brief try I've had of it!!

Whoa...the speed! It seems they're finally getting rid of all those leaks, and the slowness.

Installation worked like a charm.

---

### Post by tom56 on 2008-05-09
Slightly off-topic I guess, but not really: does anyone know if OpenOffice.org 3.0 will be added to Hardy as a Stable Release Update? It would be extremely annoying not being able to open Word files for the next 3 years!

---

### Post by steffen on 2008-05-09
> **tom56 said:**
> Slightly off-topic I guess, but not really: does anyone know if OpenOffice.org 3.0 will be added to Hardy as a Stable Release Update? It would be extremely annoying not being able to open Word files for the next 3 years!

You could make a backport request for it... Might be worth a try.

[https://launchpad.net/ubp/](https://launchpad.net/ubp/)

---

### Post by tom56 on 2008-05-10
Well, I didn't mean now, but when it hits final. But I might do that once it does.

---

### Post by KhaaL on 2008-05-19
I'm kinda dissapointed at the lack of a 64-bit release of the beta...

---

### Post by Andrew.Z on 2008-05-19
> **KhaaL said:**
> I'm kinda dissapointed at the lack of a 64-bit release of the beta...

OpenOffice.org upstream has never released a 64-bit build until [soon](http://blogs.sun.com/GullFOSS/entry/openoffice_org_builds_for_linux)

---

### Post by Joeb454 on 2008-05-20
Glad to hear they'll be building 64 bit versions soon :) I may get round to trying out the beta then :)

---

