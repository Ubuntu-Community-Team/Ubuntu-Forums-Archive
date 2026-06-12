---
title: "Two questions about PPA"
date: 2008-03-04
forum: Packaging and Compiling Programs
---

### Post by Adnarim on 2008-03-04
Hi,
I have two questions about these PPA's at launchpad.

1.) May I give other people access to my ppa and the packages I created? Is there some traffic-limit? I'm creating a package for a software which hasn't any deb-packages by now at all. So I wanna contact the author of the software if he's interested in linking to my ppa. Can other people write it in ther sources.lst and use it? Or is directlinking to the deb packages allowed?

2.) I created a package which works fine. But I did some changes because I did something wrong with the copyright file. If I now try to upload the new created package I'm always getting this error-msg:
> 
Rejected:
MD5 sum of uploaded file does not match existing file in archive
Files specified in DSC are broken or missing, skipping package unpack verification.


But the silly thing: I deleted the old package via the webfrontend of the ppa before I uploaded this version. Is there a way to really delete the old package or do I really have to use a new version-number X.X.X-2 ?

greets

---

### Post by Vorian on 2008-03-05
> **Adnarim said:**
> Hi,
I have two questions about these PPA's at launchpad.

1.) May I give other people access to my ppa and the packages I created? 

2.) I created a package which works fine. 

But the silly thing: I deleted the old package via the webfrontend of the ppa before I uploaded this version. Is there a way to really delete the old package or do I really have to use a new version-number X.X.X-2 ?

greets

answer to the first question is yes, you are welcome to share your archive.  

As to the second question, if you provide a link to your ppa, I'd be happy to look at the package.

(yes, with any upload you have to change the version with ppa's)

---

### Post by Vorian on 2008-03-05
just a follow up to versions:

it should be 0ubuntu1~ppa1
then...
0ubuntu1~ppa2
0ubuntu1~ppa3  and so on...

---

### Post by Adnarim on 2008-03-13
Yes thank you :)  That's something which should be written somewhere. PPA keeps track of the packages you uploaded even after they have been deleted.

greets

---

