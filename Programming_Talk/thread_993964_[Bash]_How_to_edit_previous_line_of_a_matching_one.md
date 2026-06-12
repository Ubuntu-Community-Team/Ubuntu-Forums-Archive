---
title: "[Bash] How to edit previous line of a matching one?"
date: 2008-11-26
forum: Programming Talk
---

### Post by Forlong on 2008-11-26
I have a text file that looks like this (segment):
```
: 181 7 64 Wie
: 188 3 61  es
* 193 7 59  ist
- 202 237
: 257 2 57 Und
: 260 8 62  zwar
: 268 4 61  bist
: 276 6 62  du
: 284 6 61  vom
: 292 8 62  We
: 300 4 61 sen
- 306
: 308 7 62 So
: 316 4 61  und
: 320 8 59  so
```
Now I want all the double spaces to become regular ones (trivial) but the previous line should then end on a space:
```
: 181 7 64 Wie 
: 188 3 61 es 
* 193 7 59 ist
- 202 237
: 257 2 57 Und 
: 260 8 62 zwar 
: 268 4 61 bist 
: 276 6 62 du 
: 284 6 61 vom 
: 292 8 62 We
: 300 4 61 sen
- 306
: 308 7 62 So 
: 316 4 61 und 
: 320 8 59 so
```
Mind the spaces after "Wie", "es", "Und" etc. now.

Does anybody have an idea how to achieve this by script?

---

### Post by geirha on 2008-11-26
This bash script should do it. It should be possible with sed and awk as well.

```

#!/bin/bash

read prevline
while read line; do
    if [[ "$line" =~ "  " ]]; then
        echo "$prevline "
        prevline=`echo "$line" | sed 's/  / /'`
    else
        echo "$prevline"
        prevline="$line"
    fi
done
echo "$prevline"

```

Run with
```
bash script.bash < input.txt > output.txt
```

Note that the [[ string =~ regex ]] syntax is bash specific so it won't work with dash/sh.

---

### Post by stroyan on 2008-11-26
You don't need to use sed for the substitution.
Bash can do a string substitution with ${v/*pattern*/*replacement*}.
```

prevline=`echo "$line" | sed 's/  / /'`
is replaced by
prevline="$line/  / "

```

---

### Post by geirha on 2008-11-26
> **stroyan said:**
> You don't need to use sed for the substitution.
Bash can do a string substitution with ${v/*pattern*/*replacement*}.
```

prevline=`echo "$line" | sed 's/  / /'`
is replaced by
prevline="$line/  / "

```

Ah, yes of course. prevline="${line/  / }". I was first attempting to do it with sed, so I got a bit locked on sed.

---

### Post by Forlong on 2008-11-26
Thanks guys, works great!

Two additional questions:
In the files I need to convert, all lines end with carriage returns and there are also some comments in the headers.

1) I need to get rid of the carriage returns e.g. like this:
```
sed -e 's/\r//g'
```
prior to the actual script, how would I be doing this at the very beginning of the script?

2) How do I tell the script to ignore all lines starting with #

---

### Post by geirha on 2008-11-26
Run the script with ```
sed 's/\r$// ; /^#/d' | bash script.bash >output.txt
```

Or if you want to do it inside the script, do
```

cr=$'\r'                   # carriage return
prevline="${prevline%$cr}" # remove an ending \r from the line, if any

```
To skip #'s, add a loop at the start that reads the first line that doesn't start with a # with:
```

read prevline
# loop until $prevline does not start with #
while [ "${prevline:0:1}" = "#" ]; do 
    read prevline
done
prevline="${prevline%$cr}"
while read line; do
    [ "${line:0:1}" = "#" ] && continue # Skip if $line starts with #
    line="${line%$cr}"
    ...

```

---

### Post by ghostdog74 on 2008-11-26
```

awk '{$1=$1}{print $0" "}' file

```

---

