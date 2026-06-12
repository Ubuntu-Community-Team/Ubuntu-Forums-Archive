---
title: "looking for libstdc++2.10-glibc2.2"
date: 2006-02-01
forum: Repositories &amp; Backports
---

### Post by rock freak on 2006-02-01
hi there i am ineed of the ib libstdc++2.10-glibc2.2.  i have tried getting it from the debain ste but it is down due to some sort of error with there server and i cant find it any were else.

can any one help at all. its so that i can get the nxclient working of my AMD64 ubuntu!!!

cheers 

Ollie

---

### Post by moopere on 2006-02-01
[QUOTE=rock freak]hi there i am ineed of the ib libstdc++2.10-glibc2.2.  i have tried getting it from the debain ste but it is down due to some sort of error with there server and i cant find it any were else.

can any one help at all. its so that i can get the nxclient working of my AMD64 ubuntu!!!

cheers 

Ollie[/QUOTE]


Is this not available in the standard ubuntu repos?  I know its there for i386 but don't have an AMD64 machine so I never checked.  

Cheers,
Craig

---

### Post by rock freak on 2006-02-01
it cud be ont he 32but one and i wud just force it to install but im not sure i know they arent in any f the repos that i hve in my list!! even a 32bit version would be ok or if someone has the source then that would be good!!

---

### Post by towsonu2003 on 2006-02-01
EDIT: ok, I missed that you have AMD64, so this reply won't be useful to you... sorry for the mistake.

I used packages.ubuntu.com to check that. It seems to be in the universe. here is the link:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libstdc%2B%2B2.10-glibc2.2&searchon=names&subword=1&version=breezy&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libstdc%2B%2B2.10-glibc2.2&searchon=names&subword=1&version=breezy&release=all)

Small print: If you decide to download it from the site instead of apt-getting, make sure you have all the dependencies and the dependencies of the dependencies (and so on) installed before installing that package.

---

### Post by rock freak on 2006-02-01
well i dont mind if its 32 becos if i can get it n deb then it cud be possible to tell it to force it through ignoring the arcatexture (sorry about spelling)

---

### Post by moopere on 2006-02-02
[QUOTE=rock freak]well i dont mind if its 32 becos if i can get it n deb then it cud be possible to tell it to force it through ignoring the arcatexture (sorry about spelling)[/QUOTE]

Did you look in the i386 repository?

I just had a squiz and its there for every release of Ubuntu in i386 only:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libstdc%2B%2B2.10-glibc2.2&searchon=names&subword=1&version=all&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libstdc%2B%2B2.10-glibc2.2&searchon=names&subword=1&version=all&release=all")

I've got no clue at all as to whether this will work under 64 bit though - good luck.

Cheers,
Craig

---

