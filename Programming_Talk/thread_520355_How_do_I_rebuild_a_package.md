---
title: "How do I rebuild a package?"
date: 2007-08-08
forum: Programming Talk
---

### Post by wersdaluv on 2007-08-08
For months and months, I have been trying to figure a way out to make synce-kde work in Feisty.

It seems to me that to make synce-kde work, I have to rebuild it after seeing [this bug report]("https://bugs.launchpad.net/ubuntu/+source/synce-kde/+bug/82455").

Please help me rebuild this package.

>  
well, it seems that it can be solved by merely rebuilding it.
- i apt-get sourced synce-kde and syncekonnector
 - did apt-get build-dep ...
 - export DEB_BUILD_OPTIONS="debug nostrip noopt"
 - compiled (apt-get source -b ...)
 - and installed (dpkg -i ...)
 - and everything works like a breeze....
so please rebuild it!

I do not understand what the quote above meant. How do I apt-get source and so on?

---

### Post by tbroderick on 2007-08-08
> **wersdaluv said:**
> 
I do not understand what the quote above meant. How do I apt-get source and so on?

It has already been rebuilt and uploaded to the servers. The bug is closed. If you are still having a problem with it, you should reopen the bug report.

---

