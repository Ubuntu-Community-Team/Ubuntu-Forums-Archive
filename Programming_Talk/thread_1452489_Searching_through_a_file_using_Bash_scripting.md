---
title: "Searching through a file using Bash scripting"
date: 2010-04-12
forum: Programming Talk
---

### Post by tjd_maximum on 2010-04-12
Hey, 

I'm pretty bad with shell scripting. I find it pretty cryptic and have never really found a good guide on it. Anyway, what I'm trying to do is pretty simple I think.

I have a file with some couple hundred lines of data in two columns. Each line looks like:

NUMBER1    NUMBER2

Now, if NUMBER1 is greater then a given value, call it MAXVAL, then NUMBER1 goes to file1, and NUMBER2 goes to file2. Otherwise, I want to ignore the line completely. 

Any ideas on a complete or partial solution? I'm sure for someone this is pretty easy. Any help would be appreciated. Thanks.

---

### Post by iponeverything on 2010-04-12
```
cat file |awk '$1 > 100 {print "echo "$1" >> /tmp/value1; echo "$2" >> /tmp/value2"}'
```

Where 100 is your maxvalue. As it is it will just print screen, pipe it to sh for it to work.

---

### Post by tjd_maximum on 2010-04-12
Thanks for the speedy reply! I really need to get better with this. . .

---

### Post by geirha on 2010-04-12
And here's how you can do it in bash

```

#!/bin/bash

maxval=100

while read -r number1 number2; do
  (( number1 > maxval )) || continue
  echo "$number1" >&3
  echo "$number2" >&4
done <file 3>file1 4>file2

```

I recommend this guide for learning bash: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

### Post by Cracauer on 2010-04-12
The shellscript solution won't do floating point, though.

---

