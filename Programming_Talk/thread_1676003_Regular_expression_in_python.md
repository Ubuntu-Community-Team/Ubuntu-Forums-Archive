---
title: "Regular expression in python"
date: 2011-01-26
forum: Programming Talk
---

### Post by lordgafal on 2011-01-26
Hi,

in my off-time lately i have been learning python and pygtk to make an application. well anyway i got stuck on a RE problem if anyone could please help

here where it gets stuck (actually dosent do anything):

```
clean_sources_lists = [item for item in listOfSrc if re.search(pattern, item)]
```

in context:

```

def cleanSrcList(self, listOfSrc):
		pattern = '^deb.'
		clean_sources_lists = [item for item in listOfSrc if re.search(pattern, item)]

```


thanks for helping

---

### Post by Arndt on 2011-01-26
> **lordgafal said:**
> Hi,

in my off-time lately i have been learning python and pygtk to make an application. well anyway i got stuck on a RE problem if anyone could please help

here where it gets stuck (actually dosent do anything):

```
clean_sources_lists = [item for item in listOfSrc if re.search(pattern, item)]
```

in context:

```

def cleanSrcList(self, listOfSrc):
		pattern = '^deb.'
		clean_sources_lists = [item for item in listOfSrc if re.search(pattern, item)]

```


thanks for helping

I think you need to show listOfSrc too.

This trivial test succeeds, anyway:

```
>>> import re
>>> [i for i in ["deb.hej", "hopp"] if re.search("^deb.", i)]
['deb.hej']
>>> 
```

But maybe you forgot to return the clean_sources_list from the function?

---

