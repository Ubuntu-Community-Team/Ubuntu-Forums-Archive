---
title: "is it possible to find hidden files with beagle?"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by sgleo87 on 2008-11-04
I just installed beagle but I noticed it doesn't find hidden files. Is there any way to make beagle show those in the search results? (using Beagle Search 0.3.8 and Intrepid Ibex)

---

### Post by sgleo87 on 2008-11-06
anyone? guess I'll just have to resort to the find command if not...

---

### Post by eljalill on 2008-12-02
Now, this is a wild but possibly educated guess, which I will post anyway, since no-one else has replied:
Bealge doesn't index hidden files, because per default it is told not to.
If you go open a bealge window, then go to seach>preferences>indexing, there is a list of files under "privacy" which are not indexed. Rather more to the bottom you'll find that the pattern /conf[0-9]+.file/ is excluded from indexing. It looks to me as if this would mean that hidden files are excluded. If you remove it from the privacy list, and have bealge index it, then you should be able to search hidden files.

---

