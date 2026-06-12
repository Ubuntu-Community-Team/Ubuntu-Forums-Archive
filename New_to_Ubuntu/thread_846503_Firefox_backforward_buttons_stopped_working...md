---
title: "Firefox back/forward buttons stopped working.."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by TaintedBllack on 2008-07-01
I was browsing myspace and all of a sudden my back and forward buttons on the browser stopped working and now they don't work at all. It was working perfectly fine before.. Really confused as to what would be causing this. I tried reinstalling firefox and it did the same.. but maybe I didn't reinstall properly..

---

### Post by alienexplorers on 2008-07-01
Didi you try making a new profile and see if that helps.  Go to [http://www.mozillazine.org/]("http://www.mozillazine.org/")
then go to the knowledge base and it explains the whole thing.

---

### Post by unutbu on 2008-07-01
Try moving your personal firefox configuration directory:

Quit firefox.
```
mv ~/.mozilla ~/.mozilla.bak
```

Then restart firefox. FF will make a new ~/.mozilla directory. You won't have any of your settings (including bookmarks), but we can see about transporting those parts if the solution works.

If the suggestion does not work, to restore your mozilla directory to its present state, run this:

```
rm -rf ~/.mozilla
mv ~/.mozilla.bak ~/.mozilla
```

---

