---
title: "Bash: Read a formated string"
date: 2010-12-22
forum: Programming Talk
---

### Post by conradin on 2010-12-22
Hi all,
I want to write a script that will monitor the 12 line in the vmstat output stream. can I do this without writing to a file?
Also, how can I monitor the data in that "column" can anyone point me to reading formated strings in bash type tutorial?



```

$vmstat 1 10
procs                      memory      swap          io     system         cpu
 r  b   swpd   free   buff  cache   si   so    bi    bo   in    cs us sy id wa
 2  5 375912  19548  17556 477472    0    1     0     0    1     1  1  0  0  1
 0  4 375912  18700  17556 478264    0    0  1044     0  774  1329  8  1  0 91
 0  5 375912  17664  17556 479168    0    0  1160     0  764  1110  8  1  0 91
 1  8 375912  15836  17568 479796    0    0  1144   840  751  1622 16  7  0 78
 0  7 375912  19340  17576 480224    0    0  1224   148  587  1958 17 18  0 65
 2  0 375912  18288  17588 481036    0    0   812     0  845  1732 18  3 21 59
 0  2 375912  15868  17588 481528    0    0  1012     0  588   941  4  1  5 90 


```

---

### Post by Crusty Old Fart on 2010-12-23
```

man awk

```

---

### Post by papibe on 2010-12-23
What he said. awk looks like the right tool for it. Check this: [Awk Introduction Tutorial]("http://www.thegeekstuff.com/2010/01/awk-introduction-tutorial-7-awk-print-examples/").
Regards.

---

### Post by Crusty Old Fart on 2010-12-25
> **conradin said:**
> Hi all,
I want to write a script that will monitor the 12 line in the vmstat output stream. can I do this without writing to a file?
Also, how can I monitor the data in that "column" can anyone point me to reading formated strings in bash type tutorial?...

A working example for your application might help:
```

#!/bin/bash
set -e

vmstat 1 10 | \
awk '$2 ~/^[^-0-9]/ {print " ",$4,"\t\t",$6,"\t\t",$9,"\t",$12} \
     $1 ~/[0-9]/ {print " ",$4,"\t",$6,"\t",$9,"\t",$12}'

exit 0

```

---

