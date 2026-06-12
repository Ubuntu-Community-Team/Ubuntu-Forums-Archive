---
title: "libboost"
date: 2005-03-23
forum: Repositories &amp; Backports
---

### Post by tyreth on 2005-03-23
Hi,

I've done an apt-get update and still see only libboost version 1.31.0:
[http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=libboost&searchon=names&subword=1&version=all&release=all](http://higgs.djpig.de/cgi-ubuntu/search_packages.pl?keywords=libboost&searchon=names&subword=1&version=all&release=all)

However, I need to have version 1.32.0, which I know debian has.  Is there a clean way to use the debian packages for this using apt-get, and have that resolve all dependancies for me?  Basically, can I add a debian testing as one of my sources and then use apt-get to get libboost?  Or is there another way?

Thanks

---

### Post by Pesho on 2005-04-05
I'd like to second that question.

---

### Post by tyreth on 2005-04-05
I added a debian source, did apt-get update, installed boost, then removed the source and did apt-get update again.

I've now been told though there's something called "pinning" which does what I want, so you might want to look into that.

---

