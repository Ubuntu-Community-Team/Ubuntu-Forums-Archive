---
title: "Cant Compile a simple C program, the &lt;stdio.h&gt; error"
date: 2009-02-11
forum: Programming Talk
---

### Post by Felguild on 2009-02-11
Hi and thanks, 

following the suggestions founded in this page, i tried  

> sudo apt-get install build-essential

because i cant compile a simple C program 

but gave me this

> WARNING: The following packages cannot be authenticated!
  libc6-dev libstdc++6-4.1-dev g++-4.1 g++ dpkg-dev build-essential
Install these packages without verification [y/N]? 

Followed by a lot of Errors like

> Err [http://co.archive.ubuntu.com](http://co.archive.ubuntu.com) feisty/main libstdc++6-4.1-dev 4.1.2-0ubuntu4
  404 Not Found [IP: 91.189.88.31 80]


any help?
Thanks

---

### Post by unoodles on 2009-02-11
looks like you are try to install from the fiesty repository.
Are you using fiesty? If so, you won't have much luck because fiesty is now unsupported.

---

### Post by Felguild on 2009-02-11
my only choice is to install a newer version of Ubuntu?

---

### Post by unoodles on 2009-02-11
Probably. the problem is that you have to download a package that contains the file stdio.h, and it doesn't exist.

---

### Post by geirha on 2009-02-11
You can still upgrade to Gutsy. Gutsy is supported till april this year. [https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

