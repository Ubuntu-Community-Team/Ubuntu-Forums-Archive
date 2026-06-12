---
title: "Converting Large Hex Strings to Decimal"
date: 2009-12-12
forum: Programming Talk
---

### Post by Xqtftqx on 2009-12-12
Hello Everybody, 

Im trying to write a bash script that can convert a large hex value to 
decimal. Im currently using:

```

DEC=`echo "ibase=16;obase=A;$HEX" | bc`

```

Which works great, except when i try a large value such as:

```

54455353535353535353535353535353535353535353535353535353535353535353535353535353535353535353535353535353535353535353535354545454545454545454545454545454545454540A

```

It comes out like:

```

38448053310021423242031825911359116476593104898313056668171557477148\ 37124892469611104711174294347565827124313134442157829158407021418675\ 97504772427121847067280967375091881587312505075318777992202

```

I dont want the "\" and Spaces in the output. How can it so it outputs just the straight decimal value?

Thanks in advance!

---

### Post by dwhitney67 on 2009-12-13
I found this to work:
```

#!/bin/bash

HEX=$1
DEC=`echo "ibase=16;obase=A;$HEX" | bc`
DEC=`echo $DEC | sed -e 's%\(\\\ \)%%g'`

echo $DEC

```
I did not spend any time researching 'bc' to determine if there is a way to suppress the output you were trying to correct.  So, to put it mildly, what I have above is a kludge.

---

### Post by geirha on 2009-12-13
According to the man-page, the environment variable BC_LINE_LENGTH determines how long a line can be before it splits it on a new line. The default is 70.
```

#!/bin/bash

hex2dec() {
    BC_LINE_LENGTH=1000 bc <<< "ibase=16;$1"
}

dec=$(hex2dec "$1")
echo "$dec"

```

---

