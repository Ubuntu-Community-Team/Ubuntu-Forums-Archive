---
title: "Simplifying a Chrome channels' versions script"
date: 2012-08-24
forum: Programming Talk
---

### Post by Intrepid Ibex on 2012-08-24
So hi.

I wrote this fairly simple script to check the latest version strings of all the 3 Chrome channels:

```
#!/bin/bash

cd /tmp
curl -sO http://dl.google.com/linux/chrome/rpm/stable/x86_64/repodata/other.xml.gz
gzip -df other.xml.gz

echo; echo -n "Stable: "
grep '\-stable' other.xml | cut -d " " -f6 | cut -d '"' -f2; echo

echo -n "Beta: "
grep beta other.xml | cut -d " " -f6 | cut -d '"' -f2; echo

echo -n "Unstable: "
grep unstable other.xml | cut -d " " -f6 | cut -d '"' -f2; echo

rm other.xml
```

Which currently produces:
```



Stable: 21.0.1180.81

Beta: 22.0.1229.14

Unstable: 23.0.1243.2
```

My question is: is there a way(s) to simplify this even further (e.g. using awk or a loop for all the three channels or something)?

---

### Post by Vaphell on 2012-08-24
```
$ awk -F\" '/pkgid/{ sub(".*-","",$4); print $4": "$10 }' other.xml
stable: 21.0.1180.81
beta: 22.0.1229.14
unstable: 23.0.1243.2
```

---

### Post by sisco311 on 2012-08-25
One-liner:

```

curl -s http://dl.google.com/linux/chrome/rpm/stable/x86_64/repodata/other.xml.gz | gzip -df | awk -F\" '/pkgid/{ sub(".*-","",$4); print $4": "$10 }'


```

---

### Post by Intrepid Ibex on 2012-08-25
Thanks guys.

---

