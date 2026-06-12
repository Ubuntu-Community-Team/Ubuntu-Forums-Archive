---
title: "SED - replace all text after a matched string"
date: 2012-12-04
forum: New to Ubuntu
---

### Post by ibizatunes on 2012-12-04
Hello

Im looking to replace text after "MapLocation=" and the add a file path eg MapLocation=/mnt1/acc/config

The reason I cant do a simple sed replace, is that path MapLocation=build_snapshot0.1.0/build 
has a number that will increment as i get new snapshot from the developers - so there isn't a static string to replace
I have tried the folling with no luck
```
egrep -i build_snapshot | xargs -0 sed -i 's|build_snapshot|/mnt1/acc/config|g'
```

If I do a simple sed replace it still has 0.1.0/build at the end
```
's|build_snapshot|/mnt1/acc/config|g'
```
resulting /mnt/acc/config/0.1.0/build
I need the final result to be

MapLocation=/mnt1/acc/config
Regardless of version numbers

Please can you help

---

### Post by steeldriver on 2012-12-04
maybe you could add [.0-9]\+ to match any combination of periods and digits?

```
echo "MapLocation=build_snapshot0.1.0/build" | sed 's|build_snapshot[.0-9]\+/build|/mnt1/acc/config|'
MapLocation=/mnt1/acc/config
```

---

### Post by ibizatunes on 2012-12-04
Many thanks - that fixed the issue

---

