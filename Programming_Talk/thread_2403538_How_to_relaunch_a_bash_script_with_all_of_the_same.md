---
title: "How to relaunch a bash script with all of the same inputs"
date: 2018-10-12
forum: Programming Talk
---

### Post by jambu-mrt on 2018-10-12
Is there a cleaner/easier way to do this?

```
#!/bin/bash
updatesFound=0

#
## Some code here to check for updates found remotely
#

if [ $updatesFound -gt 0 ]; then
    # the script running is outdated, and needs to be relaunched
    relaunchCMD="$0"
    i=1
    ARGC=$#
    while [ $i -le $ARGC ]; do
        relaunchCMD="$relaunchCMD \"${!i}\""
        i=$((i+1)); # increment input
    done
    $relaunchCMD --no-update
fi

```

Thanks!

---

### Post by edadasiewicz on 2018-10-13
Have you tried the following:

```

$0 "$@"

```

to relaunch?

---

### Post by jambu-mrt on 2018-10-15
The works perfect, I thought there was something like that, but couldn't find a reference.

Thanks!

---

