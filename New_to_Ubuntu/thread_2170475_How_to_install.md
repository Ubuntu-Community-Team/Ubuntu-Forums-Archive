---
title: "How to install???"
date: 2013-08-26
forum: New to Ubuntu
---

### Post by baker-quin on 2013-08-26
I just downloaded FileZilla3.7.3 from [https://filezilla-project.org/](https://filezilla-project.org/). This gave me the FileZilla_3.7.3_i586-linux-gnu.tar.bz2 file in ~/Downloads. I then used archive manager to extract into ~/Downloads as well and named the directory FileZilla3. Now I have no idea what I'm doing... I think I'm looking for .deb file to execute for the installation but I'm not seeing one even with ls -a... From what I understand looking from [https://forum.filezilla-project.org/viewtopic.php?f=3&t=2172](https://forum.filezilla-project.org/viewtopic.php?f=3&t=2172), I need to execute the filezilla binary which I believe I've found here 

code: ~/Downloads/FileZilla3/bin$ ls -a.  ..  filezilla  fzputtygen  fzsftp

I've also found a few sites for installing with repository but I'm not having luck with them either. [http://www.noobslab.com/2012/11/install-filezilla-in-ubuntu.html](http://www.noobslab.com/2012/11/install-filezilla-in-ubuntu.html) only when I do the add-apt-repository command I get this:
uh... nevermind... copied and pasted  this and it worked. I did it before without copying and I must have made a mistake or something. So this did actually work but for the purpose of education, how would I have done it the other way?

---

### Post by sandyd on 2013-08-26
> **baker-quin said:**
> I just downloaded FileZilla3.7.3 from [https://filezilla-project.org/](https://filezilla-project.org/). This gave me the FileZilla_3.7.3_i586-linux-gnu.tar.bz2 file in ~/Downloads. I then used archive manager to extract into ~/Downloads as well and named the directory FileZilla3. Now I have no idea what I'm doing... I think I'm looking for .deb file to execute for the installation but I'm not seeing one even with ls -a... From what I understand looking from [https://forum.filezilla-project.org/viewtopic.php?f=3&t=2172](https://forum.filezilla-project.org/viewtopic.php?f=3&t=2172), I need to execute the filezilla binary which I believe I've found here 

code: ~/Downloads/FileZilla3/bin$ ls -a.  ..  filezilla  fzputtygen  fzsftp

I've also found a few sites for installing with repository but I'm not having luck with them either. [http://www.noobslab.com/2012/11/install-filezilla-in-ubuntu.html](http://www.noobslab.com/2012/11/install-filezilla-in-ubuntu.html) only when I do the add-apt-repository command I get this:
uh... nevermind... copied and pasted  this and it worked. I did it before without copying and I must have made a mistake or something. So this did actually work but for the purpose of education, how would I have done it the other way?

Filezilla is already in the software center, you do not need to add additional repositories (or even go to the command line) to install it.
Simply open the Ubuntu Software Center, and search for 'filezilla'

---

### Post by baker-quin on 2013-08-26
I heard that the software centers FileZilla wasn't up to date from a website. I don't remember which one. Anyway, that is why I was trying other methods to get the most current. Yes, I see now that the Software Center one is up to date but I already have it installed now through the ppa listed and it is checked off in the Software Center so I'm assuming this means I have the same one. My concern now is that I will again run into a [COLOR=#000000].tar.bz2 type file or similar where I have to extract files and then install somehow and I don't understand how this works. [/COLOR]

---

### Post by sandyd on 2013-08-26
> **baker-quin said:**
> I heard that the software centers FileZilla wasn't up to date from a website. I don't remember which one. Anyway, that is why I was trying other methods to get the most current. Yes, I see now that the Software Center one is up to date but I already have it installed now through the ppa listed and it is checked off in the Software Center so I'm assuming this means I have the same one. My concern now is that I will again run into a [COLOR=#000000].tar.bz2 type file or similar where I have to extract files and then install somehow and I don't understand how this works. [/COLOR]

Most software is in the software center - those that aren't are likely in a PPA somewhere

---

