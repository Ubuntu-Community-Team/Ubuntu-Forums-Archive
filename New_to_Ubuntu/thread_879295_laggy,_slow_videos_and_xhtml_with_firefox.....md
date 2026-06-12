---
title: "laggy, slow videos and xhtml with firefox...."
date: 2008-08-03
forum: New to Ubuntu
---

### Post by jcway212 on 2008-08-03
Has anyone else had problems with firefox? I seem to be having issues with lag...not sure if it's Ubuntu or Firefox?

example 
[http://www.mojaveexperiment.com/]("http://www.mojaveexperiment.com/")

The menu seems very laggy.


Thanks,
Paul

---

### Post by northern lights on 2008-08-04
That link works for me.

Navigate to "System > Administration > Software Sources". Enable all
repositories but 'proposed' and 'backports'.

Then run ```
sudo apt-get update && sudo apt-get autoremove totem-mozilla && sudo apt-get install mozilla-mplayer flashplugin-nonfree
```

In case you might also need wma/wmv support:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update && sudo apt-get install w32codecs
```

---

### Post by mcduck on 2008-08-05
I don't see any XHTML on that page, just Flash.. ;)

---

