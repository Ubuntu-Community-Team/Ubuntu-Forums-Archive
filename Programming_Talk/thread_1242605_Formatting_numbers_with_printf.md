---
title: "Formatting numbers with printf"
date: 2009-08-17
forum: Programming Talk
---

### Post by kaibob on 2009-08-17
I am attempting to format numbers in a bash shell script as follows:

* Numbers are rounded to 2 decimal places.

* Trailing zeros are removed.

* Thousand separators are used (commas in my locale).

To give some examples:

1) 6 is formatted as 6

2) 6.60 is formatted as 6.6

3) 6.666 is formatted as 6.67

4) 6666 is formatted as 6,666

I tried two alternatives as shown below. The first works but only if the number contains 5 digits or less. The second works but is cumbersome. 

```
printf "%'g\n" "${number}"

printf "%'.2f\n" "${number}" | sed 's/\.00$// ; s/\(\.[1-9]\)0$/\1/'
```

Is there an easier way to do this?

As an aside, I'm just learning shell scripting, so another language is not an option right now.

Thanks for the help.

---

### Post by ibuclaw on 2009-08-17
This is a rather overblown version using nothing but bash string manipulating (this **won't** work in sh)
```
#!/bin/bash

function print
{
    shopt -s extglob
    fmt=

    # split
    h=${1%%.*}
    t=
    if [ ${#h} -lt ${#1} ]; then
        t=${1##*.}
    fi

    # 06.6 -> 6.6
    h=${h/#+(0)/}

    # 6.60 -> 6.6
    t=${t/%+(0)/}

    # 6666 -> 6,666
    if [ "${#h}" -gt 3 ]; then
        tmp=
        for i in `seq 1 ${#h}`; do
            if [ $(( (${#h}-$i) % 3)) -eq 0 ] && [ ${#h} -ne $i ]; then
                tmp="$tmp${h:$i-1:1},"
            else
                tmp="$tmp${h:$i-1:1}"
            fi
        done
        h=$tmp
    fi

    # 6.666 -> 6.67
    if [ "${#t}" -ge 3 ]; then
        tmp=${t:1:1}
        if [ ${t:2:1} -ge 5 ]; then
            let tmp++
        fi
        t="${t:0:1}$tmp"
    fi

    # join
    if [ ${#t} -gt 0 ]; then        
        fmt="$h.$t"
    else
        fmt="$h"
    fi  

    echo $fmt
    shopt -u extglob
}

# Basic Criteria
print 6
print 6.60
print 6.666
print 6666

# Show that all features are working
print 00003121232.6660000

exit 0;

```

:)
Regards
Iain

---

### Post by stroyan on 2009-08-17
You could use the bash ${v%pattern} feature to remove the trailing "." and "0"s.
You need to control the locale to make sure printf does thousands grouping.
```
p () 
{ 
    local p=$(LC_NUMERIC=en_GB.utf8 printf "%'.2f" $1);
    p="${p%0}";
    p="${p%0}";
    p="${p%.}";
    printf "%s\n" "$p"
}
```

---

### Post by kaibob on 2009-08-17
Thanks tinivole and stroyan. I tried both suggestions, and they work great. I wrote my original script in part to learn, so I'll benefit from both responses. 

In studying tinivole's response, I noticed that my original post was in error. There was no need to round numbers to 2 decimal places, because this was done elsewhere in the script. This complicated things unnecessarily, and I should have caught and corrected this before posting. Sorry!

@stroyan. I was fascinated by the simplicity of your approach. I pasted it into my script, made a few necessary changes to existing portions of the script, and verified that everything worked as intended. 

Thanks again.

---

