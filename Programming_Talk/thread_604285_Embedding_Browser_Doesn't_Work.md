---
title: "Embedding Browser Doesn't Work"
date: 2007-11-06
forum: Programming Talk
---

### Post by tonyr1988 on 2007-11-06
I'm trying to embed a browser in one of my SWT Java applications. It worked just fine in Feisty, but it's broken in Gutsy. It gives me the error:

> No more handles [Unknown Mozilla path (MOZILLA_FIVE_HOME not set)]

My MOZILLA_FIVE_HOME is currently set to /usr/lib/firefox. Two questions:

1) Is this the correct setting?, and
2) If it is, could be there be something preventing Java from "seeing" it? I'm using the NetBeans IDE, if that would make a difference.

I'm really hoping to get this up and working again, and one more Gutsy problem will be solved (I still have several more to go, though :P).

---

### Post by tonyr1988 on 2007-11-06
Small bumpedy bump.

Did Gutsy break this for anyone else?

---

### Post by tenmillionmilesaway on 2007-11-06
I remember reading somewhere that the firefox that comes with most linux distros isn't really suitable for embeding.  I could be wrong though.  You could try the mozilla from here: [http://www.mozilla.org/releases/](http://www.mozilla.org/releases/) which is defiantly suitable.

First though I would confirm that ```
echo $MOZILLA_FIVE_HOME
``` is pointing to the right location.

Hope this helps

Richard

---

