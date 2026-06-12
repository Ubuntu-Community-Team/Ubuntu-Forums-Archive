---
title: "Problems with Kdevelop headers"
date: 2005-08-07
forum: Programming Talk
---

### Post by Luggy on 2005-08-07
Presently I'm just trying to create a Simple KDE Application (from new project C++ -> KDE -> Simple KDE Application). I want to test it to make sure that everything is in tip top shape; Run automake & friends works fine but when I try to Run configure I get an error message.
```
checking for KDE... 
configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
*** Exited with status: 1 ***
``` 

I've checked out this thread [HTML]http://ubuntuforums.org/showthread.php?t=3505&highlight=kdevelop+headers[/HTML]  and when I perform ```
apt-cache search qt-mt
``` and I try and apt-get install the files, I seem to install one and have to remove the other. Can anyone lend me some advice?

---

### Post by wpp42000 on 2006-02-12
Although this is an old post, I just had the same problem.  I found a solution in another thread (copied below).  Hope this helps.
--------------------------------------------------------------------------------

Which repository do you use for KDE 3.5? The Kubuntu packages for KDE 3.5? Looking at this repo shows that it contains all those *-dev files which you need.

Oops: Saw your last message too late.
If you don't know what packages to install, the headers are all distributed in those -dev files, for example libkde4-dev contains all headers for the kdelibs. kdebase-dev contains the headers of kdebase and so on. A nice way to install -dev packages is via command line with something like

Code:
$ apt-get build-dep kdepim

That command would install all packages which you need to build kdepim from source. Of course this only works for packages which are already in the repository.

--------------------------------------------------------------------------------
Last edited by asimon : 4 Weeks Ago at 09:14 AM.

---

