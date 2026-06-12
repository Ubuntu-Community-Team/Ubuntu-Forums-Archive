---
title: "correctly round in bash"
date: 2010-01-03
forum: Programming Talk
---

### Post by roccivic on 2010-01-03
10 divided by 6 is roughly 1.67, which should be rounded to 2, but bash rounds all numbers down.
For example:[PHP]echo $((10/6))[/PHP]will output 1.

How could this be solved?

Any help with this is much appreciated.

---

### Post by Reiger on 2010-01-03
So there is an implicit floor() in (10/6)? In that case: $((10/6) + 0.5) ought to do.

---

### Post by Axos on 2010-01-03
The man page says bash only does integer math. You'll need to use some other program to do the math and backquote the result into a string variable.

---

### Post by roccivic on 2010-01-03
> **Axos said:**
> The man page says bash only does integer math. You'll need to use some other program to do the math and backquote the result into a string variable.
And I would be very happy with an integer result as long as it's rounded, not floored.

> **Reiger said:**
> So there is an implicit floor() in (10/6)? In that case: $((10/6) + 0.5) ought to do.

thanks, but this actually generates a syntax error...

---

### Post by Axos on 2010-01-03
You can get the remainder with the % operator. You can use that to determine whether to round up or down.

---

### Post by roccivic on 2010-01-03
Oh, the modulus, of course. Thank you.

Although I just got it working anyway.
[PHP]#!/bin/bash

x=10
y=6

a=$(($x/$y))
b=$((($x*10)/$y))
c=$(($b-($a*10)))
if [ "$(($c<5))" == "0" ]; then
  a=$(($a+1))
fi

echo $a[/PHP]

---

### Post by ghostdog74 on 2010-01-04
use awk

```

awk 'BEGIN{print int((10/6)+0.5)}'

```

---

### Post by ProgramErgoSum on 2010-01-04
I was looking around for a similar question. And, I found the [bc](http://www.novell.com/coolsolutions/tools/17043.html) command. Try this :
```

#calc
ops="594307/1024^2"
echo "scale=4; ${ops}" | bc ;
exit 0

```

---

### Post by kaibob on 2010-01-04
A while back I couldn't get bash or the bc utility to round correctly and did a bit of googling. For my very-simple needs, I finally decided on awk, primarily because I found a one-liner that was easily changed for floating point calculations. 

> awk 'BEGIN { printf "%.0f\n", 10/6 }'
2
awk 'BEGIN { printf "%.1f\n", 10/6 }'
1.7
awk 'BEGIN { printf "%.2f\n", 10/6 }'
1.67

I don't know if it's appropriate to use printf "%.0f" when rounding to a whole integer but it does work. I tried using printf "%d" but it rounded the above calculation down to 1.

---

### Post by akvino on 2010-01-04
just use awk.

---

