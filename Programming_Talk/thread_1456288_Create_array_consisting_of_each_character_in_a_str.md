---
title: "Create array consisting of each character in a string"
date: 2010-04-17
forum: Programming Talk
---

### Post by kaibob on 2010-04-17
I'm trying to create a bash array in which each character in a string is an element in the array. The number of characters in the string vary. I've come up with two solutions that work but seem overly complicated. Is there an easier way to do this? Thanks for the help!

SOLUTION 1

```
string=abcde ; array=( $(sed 's/./& /g' <<< $string) ) ; echo ${array[1]}
```

SOLUTION 2

```
#!/bin/bash

string=abcde

for (( i=1 ; i<=${#string} ; i++ )) ; do
   j=$((i-1))
   letter=${string:${j}:1}
   array+=( "$letter" )
done

echo ${array[1]}
```

---

### Post by falconindy on 2010-04-17
Unless there's some way to abuse the IFS to split unconditionally on anything, I think the sed solution may be the most concise.

On the other hand, you're essentially creating an array in your Bash solution already with ${string:$i:1} -- is there a reason you can't just use that?

---

### Post by soltanis on 2010-04-17
Dunno about BASH but in Awk there is totally a way to abuse the Field Separator.

```

# awk code
BEGIN { FS="" }
# do things

```

---

### Post by kaibob on 2010-04-17
> **falconindy said:**
> Unless there's some way to abuse the IFS to split unconditionally on anything, I think the sed solution may be the most concise.

Changing the IFS is what I originally had in mind. Something along the lines of:

```
IFS='???' ; string=abcde ; array=( $string )
```

But, I spent quite a bit of time researching IFS and couldn't find anything. 

> **falconindy said:**
> On the other hand, you're essentially creating an array in your Bash solution already with ${string:$i:1} -- is there a reason you can't just use that?

This is what I ended up doing in the actual script (which really was not of much importance). But, this issue has stayed in my mind for a few days, so I thought I would ask if there's an easier solution that creates an array. 

Thanks for the response.

---

### Post by geirha on 2010-04-17
You can also use a while read loop.
```
#!/bin/bash

string="String    with some  ôdd chars"$'\n'"foo * µ"

unset a i
while read -r -n1 -d ''; do a[i++]=$REPLY; done <<< "$string"

printf "[%s]" "${a[@]}"

# Output:
[S][t][r][i][n][g][ ][ ][ ][ ][w][i][t][h][ ][s][o][m][e][ ][ ][ô][d][d][ ][c][h][a][r][s][
][f][o][o][ ][*][ ][µ][
]
```

The <<< will add a trailing newline which you might want to remove afterwards.

---

### Post by kaibob on 2010-04-17
geirha,

Thanks for the response. You've helped me with some bash issues before and have always had a good solution. So, in this case, I can be confident that there is not the really-simple solution I thought might exist. 

As an aside, I had to study your suggested command before I understood how it worked. It is probably the best solution because it does not use an external command, as in my solution 1, and is simpler than my solution 2.

Thanks again.

kaibob

---

