---
title: "Install Kopete 0.12 Unofficial Deb"
date: 2006-06-06
forum: Outdated Tutorials &amp; Tips
---

### Post by ZZambia on 2006-06-06
Hi guys, 
I was using for months Kopete in its SVN and later in 0.12-beta{1,2} versions under dapper. During last days it was released a final 0.12 version (0.12.0) but with NO Dapper/Breezy/Hoary DEB package.

Also, KDE 3.5.3 lacks of support of 0.12 version too. So I decided to add a custom "debian" section to standard Kopete source release and I built a DEB package.

I'm attaching it for your delight.

Kopete 0.12.0 Unofficial DEB package
[http://www.dpcontrol.it/debpkgs/kopete_0.12.0_i386.deb](http://www.dpcontrol.it/debpkgs/kopete_0.12.0_i386.deb)

ATTENTION !!!!!! This package will break kdenetwork (both 4:3.5.2-... and 4:3.5.3-...) meta-package. When prompted, you can unistall it 4sure, but keep in mind what you've done with this action. Also, ChangeLog in package is uncomplete.  Grin

---

### Post by Arkady on 2006-06-08
Thanks for the .deb!

---

### Post by jpetso on 2006-06-13
The package seems to work fine (thanks a great deal) but, as you said, it breaks kdenetwork, and worse, on every dist-upgrade the official 3.5.x version gets installed again, because its version number is higher.

The solution to both of these problems is giving the package a proper version number that is higher than 3.5.x. I modified your package so it wears the number 3.6.0. (There isn't gonna be a KDE 3.6, and in principle, Kopete 0.12 is actually Kopete 3.6.0. So this should be ok.)

Kopete 0.12.0 Unofficial DEB package for Ubuntu Dapper/LTS (with version number 3.6.0)
[http://stud4.tuwien.ac.at/~e0127236/devel/kopete_4%253a3.6.0-0ubuntu0.1_i386.deb](http://stud4.tuwien.ac.at/~e0127236/devel/kopete_4%253a3.6.0-0ubuntu0.1_i386.deb)

---

### Post by ZZambia on 2006-06-15
I've found a suitable solution without using fake version numbers (3.6.0 or similar). I've just used a composite numbering scheme like 5:3.5.3 (so we got the respect of REAL kopete/kde version and our version number is higher than the one in dapper repositories that is now 4:3.5.3).

Here you are the DEB package:

Kopete 5:3.5.3-ubuntu0 Unofficial DEB package
**[http://www.dpcontrol.it/debpkgs/kopete_3.5.3-ubuntu0_i386.deb](http://www.dpcontrol.it/debpkgs/kopete_3.5.3-ubuntu0_i386.deb)**

---

### Post by l.capriotti on 2006-06-19
@ZZambia: many tks for your package.

When I try to connect to gtalk with my gmail account I always receive a TSL error. 
I am behind a restrictive firewall allowing connections to port 80 and 443 only, but gaim works fine by specifying that the connection have to be talk.google.com and port 80. 

Anyone facing this?

Cheers

Luigi

Update: connecting to port 443 works fine.

---

### Post by jpetso on 2006-06-20
[QUOTE=ZZambia]I've found a suitable solution without using fake version numbers (3.6.0 or similar). I've just used a composite numbering scheme like 5:3.5.3 (so we got the respect of REAL kopete/kde version and our version number is higher than the one in dapper repositories that is now 4:3.5.3).[/QUOTE]
Well, I don't necessarily find that more suitable. That's because:
a) Kopete is 3.5.3 just as little as it's 3.6.0
b) Kopete 0.12 doesn't require KDE 3.5.3, it also runs down to KDE 3.3. (At least from source. Do you know if your package also runs on Breezy?)
c) Wasn't the x in x:3.y.z indicating a change in binary compatibility? Which didn't happen with Kopete 0.12.
d) What are you going to do with minor releases like 0.12.1? With the 3.6.x versioning scheme, at least the minor number is right.
...and finally,
e) Kopete 0.12 is really Kopete 3.6.0. If KDE 3.6 would be released (which is doesn't) then Kopete 0.12 would have been part of it and appeared as 3.6.0 in the official repositories. In this regard, 3.6.0 is the most accurate version number (besides 0.12) that we can find.

But all of this shall not belittle your work, I totally enjoy the 0.12 release thanks to your package.

---

### Post by l.capriotti on 2006-06-26
@ZZambia:
can you confirm that the package does not include Jingle support?

Cheers

Luigi

---

### Post by Hobbsee on 2006-06-28
what were these debs made with?

Were they properly debianized, or did you use checkinstall to make them?

If they're made with checkinstall, they should not be redistributed, as the dependancies are guessed, and are usually wrong.

Properly made files can be found here:  (still no jingle support yet)
[http://kubuntu.org/~jriddell/kopete/](http://kubuntu.org/~jriddell/kopete/)

---

### Post by l.capriotti on 2006-07-19
> **Hobbsee said:**
> what were these debs made with?
Properly made files can be found here:  (still no jingle support yet)
[http://kubuntu.org/~jriddell/kopete/](http://kubuntu.org/~jriddell/kopete/)
Any chance to have a 0.12.1 deb file?

TIA
Luigi

---

### Post by mecrip on 2006-07-26
hello! I've built a kopete 0.12.1 package, via checkinstall.
it's here [http://www.mirkuz.net/?p=306]("http://www.mirkuz.net/?p=306")

****
UPDATE: now i've got a kopete 0.12.2 package, check it out: [http://www.mirkuz.net/?p=319]("http://www.mirkuz.net/?p=319")

---

