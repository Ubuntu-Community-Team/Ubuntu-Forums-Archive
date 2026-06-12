---
title: "sh script, bad substitution"
date: 2010-05-06
forum: Programming Talk
---

### Post by 8Kuula on 2010-05-06
Script css-update-mapcycle:
```
#! /bin/sh                                                                                               

cd ~/srcds-cs/cstrike/maps

rm ../mapcycle.txt                                                                                      

MAPS=`ls -1 *.bsp`

for name in $MAPS
do
    echo ${name/.bsp/} >> ../mapcycle.txt
done

```

executing:
```

bunbun@gatekeeper:~/scripts# ./css-update-mapcycle
./css-update-maplist: 12: Bad substitution

```

So what is wrong? Script worked fine in Debian 5.0 but not with ubuntu server 10.04.

---

### Post by Portmanteaufu on 2010-05-06
The difference between OSs *might* be your shebang line. In Ubuntu, if I recall correctly, /bin/sh is a soft-link to "dash", a shell that is similar to but different from "bash". In Debian, /bin/sh probably points to regular bash.

I don't have access to a shell at the moment, so I'm afraid I can't check whether this fixes it for you. Just replace your first line with
```
#!/bin/bash
``` and give that a run.

---

### Post by 8Kuula on 2010-05-06
yes, works now, thanks :)

---

### Post by torgbaskar on 2011-03-16
> **8Kuula said:**
> yes, works now, thanks :)

it works for me, thanks !

---

