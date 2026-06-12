---
title: "assign multiline grep output to array var in bash?"
date: 2010-08-17
forum: Programming Talk
---

### Post by texaganian on 2010-08-17
I'm feeling pretty stupid but I can't seem to achieve what I want to do.

I want to assign each line returned by grep to a separate element of an array in bash.

I thought this would do it
```

IFS=$(echo -en "\n\b")
array=$(grep x testfile)

```

but instead this puts all of the lines into array[0] with embedded newlines.

Tis driving me nuts.

---

### Post by Bachstelze on 2010-08-17
You're missing the outwards parentheses in your array declaration:

```
bash-3.2$ cat foo.txt
foo
bar
baz
bash-3.2$ foo=( $(grep ba foo.txt) )
bash-3.2$ echo ${foo[0]}
bar
bash-3.2$ echo ${foo[1]}
baz

```

No need to change $IFS.

---

### Post by texaganian on 2010-08-17
> **Bachstelze said:**
> You're missing the outwards parentheses in your array declaration:

```
bash-3.2$ cat foo.txt
foo
bar
baz
bash-3.2$ foo=( $(grep ba foo.txt) )
bash-3.2$ echo ${foo[0]}
bar
bash-3.2$ echo ${foo[1]}
baz

```

No need to change $IFS.

Thanks for pointing that out.

Alas, doesn't solve my problem. Of course, I failed to explain my problem correctly.

The issue is that the lines I'm grepping contain white space. Your suggestion parses each word into a separate array element.

If you create foo.txt like this
```

line 1
line 2
line 3
this is the end, my friends.

```
it will be easy to see the issue.

I need a solution which will put one _line_ (complete with internal white space) in each array element.

---

### Post by Bachstelze on 2010-08-17
Then you do need to change IFS:

```
bash-3.2$ cat foo.txt 
line 1
line 2
line3
not a l1ne
bash-3.2$ IFS="
> "
bash-3.2$ foo=( $(grep line foo.txt) )
bash-3.2$ echo ${foo[0]}              
line 1
bash-3.2$ echo ${foo[1]}
line 2
bash-3.2$ echo ${foo[2]}
line3
bash-3.2$ echo ${foo[3]}


```

Apparently you can't store a newline into IFS with $(echo...).

---

### Post by ghostdog74 on 2010-08-17
do this
```

IFS=$'\n'
var=( $(grep "." file) )

```

Or just pure bash
```

#!/bin/bash
i=0
while read -r line
do
 case "$line" in
  *pattern*)
   var[((i++))]="$line"
 esac
done <"file"
echo "${var[@]}"


```

otherwise, if you have no need for those grepped lines anywhere else in your script, then skip the array storage.

---

