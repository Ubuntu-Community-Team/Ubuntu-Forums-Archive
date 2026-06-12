---
title: "Reading a file and assigning each line to a variable"
date: 2013-02-18
forum: Programming Talk
---

### Post by cbillson on 2013-02-18
I have a file and i'd like to be able to read it, taking each line to a variable as dictated by the file:

structure:

[INDENT]var1:result1
var2:result2
var3:result3
[/INDENT]I'd like each of these to represent

[INDENT]var1=result1
var2=result2
var3=result3
[/INDENT]I think i know how to split these up using : as a seperator, but i'm not sure where to start on taking one of the elements as the variable name.

Cheers
Chris

---

### Post by Vaphell on 2013-02-18
you haven't even mentioned the language

assuming bash, i'd use associative arrays where the data is accessible via ${array[name]}

```
$ cat vars.txt
a:1
b:2
$ declare -A list
$ list=()
$ while IFS=: read -r n v; do list+=( [$n]="$v" ); done < vars.txt
$ echo ${list[a]}
1
$ for e in ${!list[@]}; do echo $e = ${list[$e]}; done
a = 1
b = 2
```

another way would be to use *source*, but that inlines the input file/data as if it was a part of the script itself, so you should avoid anything potentially harmful. Sed is required to translate x:y format to x=y understood by bash.

```
$ cat vars.txt
a:1
b:2
$ sed 's/:/=/' vars.txt
a=1
b=2
$ source <( sed 's/:/=/' vars.txt )
$ echo $a
1

```

---

### Post by Bucky Ball on 2013-02-18
*Thread moved to **Programming Talk**.*

---

### Post by rnerwein on 2013-02-18
> **cbillson said:**
> I have a file and i'd like to be able to read it, taking each line to a variable as dictated by the file:

structure:
[INDENT]var1:result1
var2:result2
var3:result3
[/INDENT]I'd like each of these to represent
[INDENT]var1=result1
var2=result2
var3=result3
[/INDENT]I think i know how to split these up using : as a seperator, but i'm not sure where to start on taking one of the elements as the variable name.

Cheers
Chris
hi
use sed -i to change the ":" in the file (persistent)

sed [COLOR=Red]-i[/COLOR] 's/:/ = /g' your_file.txt

gives you var1 = result1
if you don't want the space - delete it in the replacement.
ciao

---

### Post by evilsoup on 2013-02-18
```

while read f
do
    key="$(sed -e 's/\(.*\):.*/\1/' <<<"$f")"
    value="$(sed -e 's/.*:\(.*\)/\1/' <<<"$f")"
    let "$key"="$value"
done <infile.txt

##  If you don't value readability, you can put this in a single line:

while read f; do let "$(sed -e 's/\(.*\):.*/\1/' <<<"$f")"="$(sed -e 's/.*:\(.*\)/\1/' <<<"$f")"; done <infile.txt

```Vaphell's solution is better, though, since arrays are more suited to this sort of thing, and it's also pure bash, and so should be faster.

EDIT: Although, speaking of pure bash, this come to mind...

```

while read f
do
    key="${f%:*}"
    value="${f#*:}"
    let "$key"="$value"
done <infile.txt

## or, on a single line:

while read f; do let "${f%:*}"="${f#*:}"; done <infile.txt

```

---

