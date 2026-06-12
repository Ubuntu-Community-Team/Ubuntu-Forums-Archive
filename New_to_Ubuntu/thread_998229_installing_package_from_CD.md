---
title: "installing package from CD"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by strueb on 2008-11-30
Forgive a eral newbie, but I have what I think is an apt question.

There are a couple packages I'd like to install (pan for newsgroups) and rdesktop.  The pan install is a tar.gz file, and the rdesktop is an rpm.  Since I've downloaded them, I've copied them to CD, and I'd like to install from the CD if possible.

1.  Should I use apt (aptget) to do the installs?  Or some other (at this point unknown application)?

2.  Whichever I should use, is there a way to point it to the cd?

3.  Will the same app work with the rpm AND the tar files?  Or do I need to unzip the tar file?  (I suspect I do, in which case I'd rather get the files off the cd and someplace where ubuntu will recognize them.  So, 3.a - where might that be?)

Sorry about the absolute dummy questions.  And thank you very much in advance
:)

---

### Post by oldos2er on 2008-11-30
Don't you have an internet connection on this box?

---

### Post by strueb on 2008-12-02
> **oldos2er said:**
> Don't you have an internet connection on this box?

Yes, I do. (finally) In that case, how do I install from the internet?  (I just figured that I had the CD;  I'd try to use it.  I had created it before I got the wireless connection working.)

Thanks!

---

### Post by LowSky on 2008-12-02
Go to System > Admin > software sources, check the box for CD at the bottom

---

### Post by LowSky on 2008-12-02
> **strueb said:**
> Yes, I do. (finally) In that case, how do I install from the internet?  (I just figured that I had the CD;  I'd try to use it.  I had created it before I got the wireless connection working.)

Thanks!


you should be able to click  install and it will grab the packages automatically, if not let us know we can fix your system

---

### Post by oldos2er on 2008-12-02
rdesktop seems to be installed by default in 8.10.

 For Pan, copy and paste this command into a terminal:

 sudo aptitude update && sudo aptitude install pan

---

### Post by strueb on 2008-12-03
> **oldos2er said:**
> rdesktop seems to be installed by default in 8.10.

 For Pan, copy and paste this command into a terminal:

 sudo aptitude update && sudo aptitude install pan


Ahh!  Thank you all.  I muchly appreciate the information!  I'll give these a shot.  (and I'll see about bringing up rdesktop, then, too.

:p

---

