---
title: "bash script"
date: 2011-08-31
forum: Programming Talk
---

### Post by abraxas334 on 2011-08-31
I have a set of files called t1.sh t2.sh t3.sh...etc
they are submission scripts to a cluster
so i would submit one as qsub t1.sh
now i want some kind of for loop that does it for all of them in one go. How does that work?

Thanks

---

### Post by Smart Viking on 2011-08-31
Something like this maybe:
```
for i in {1..100}; do echo qsub\ t$i.sh; done
```

---

### Post by abraxas334 on 2011-08-31
echo just prints it to the screen, but doesn't actually execute this command.

---

### Post by Habitual on 2011-08-31
use
```
for i in {1..100}; do qsub\ t$i.sh; done
```

for the real run of the commands.

---

### Post by Smart Viking on 2011-08-31
The reason I used echo, is because you should never trust too much in your own knowledge. So if there were eventual errors or mistakes, they would be caught before any harm was done. I've never heard about the qsub program, so I figured it's best to be on the safe side.

---

