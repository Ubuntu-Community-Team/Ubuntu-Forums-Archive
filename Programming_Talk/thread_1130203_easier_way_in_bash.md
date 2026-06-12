---
title: "easier way in bash?"
date: 2009-04-19
forum: Programming Talk
---

### Post by PGScooter on 2009-04-19
Hi,

Suppose I have "'one', 'green', 'sevenkj'" in an array. Is there an easier way rather than one by one doing the following?

```

 if [ "$aname" = 'one' ] || [ "$aname" = 'green' ] || [ "$aname" = 'sevenkj' ] || [ "$aname" = 'tricky' ] || [ "$aname" = 'slot' ] || [ "$aname" = 'fish' ] || [ "$aname" = 'flick' ] || [ "$aname" = 'plughome' ]; then

```

thanks!

---

### Post by PhrankDaChickenGeek on 2009-04-19
Try something along the lines of:

```

RESULT=$(echo $ARRAY | grep "$aname")
if [ "$RESULT" != "" ]; then

```
If $RESULT contains something, then $aname was found in the array. Otherwise $RESULT will = ""

---

### Post by jpkotta on 2009-04-19
You can also do something like:
```

#!/bin/bash

declare -a names
names=(one green sevenkj)

is_name_valid()
{
    a_name="$1"
    valid=0
    for ((i = 0; i < ${#names}; i++)) ; do
	if [[ "$a_name" = "${names[$i]}" ]] ; then
	    valid=1
	    break
	fi
    done
    echo $valid
}

echo $(is_name_valid "foo")
echo $(is_name_valid "one")
```

Honestly, I like PhrankDaChickenGeek's better, but this way you don't need to run grep.

---

### Post by PGScooter on 2009-04-19
phrank and jpkotta,

thank you both for your help! phrank, that is a very creative and quick way.

jpkatta, are there any main reasons why I would not want to use grep? is it more reliable/faster to use simpler commands?

---

### Post by Arndt on 2009-04-20
> **PGScooter said:**
> phrank and jpkotta,

thank you both for your help! phrank, that is a very creative and quick way.

jpkatta, are there any main reasons why I would not want to use grep? is it more reliable/faster to use simpler commands?

Beware if one of the entries might match the other, for example if you have both "green" and "greenish". Anchoring the grep search (using ^ and $) may be enough to solve that problem.

---

### Post by PGScooter on 2009-04-20
> **Arndt said:**
> Beware if one of the entries might match the other, for example if you have both "green" and "greenish". Anchoring the grep search (using ^ and $) may be enough to solve that problem.

ah, indeed I had not thought of that! thank you

---

### Post by odyniec on 2009-04-20
Here's another method -- no grep, just bash. Example of checking for an element that exists in the array:
```
$ array=(red green blue)
$ a=" ${array[*]} "
$ aname=blue
$ [ "$a" == "${a/ $aname /}" ]
$ echo $?
1
```

And for one that doesn't exist in the array:
```
$ aname=yellow
$ [ "$a" == "${a/ $aname /}" ]
$ echo $?
0
```

---

### Post by PGScooter on 2009-04-20
odyniec,

would you mind explaining your code please? I do not understand the 2nd and 4th lines of your first code bracket. Thanks

---

### Post by odyniec on 2009-04-20
In this line:
```
a=" ${array[*]} "
```
${array[*]} expands to all elements of $array, separated by spaces. A space is also added at the beginning and at the end, making $a equal to " red green blue ". The added spaces are there to address the "green" vs. "greeninsh" issue that Arndt pointed out.

```
[ "$a" == "${a/ $aname /}" ]
```
${a/ $aname /} is a bash construct meaning: replace the first occurrence of " $aname " within $a with an empty string.

The whole command does a comparison of $a before and after the replacement. If the two are not equal ($? set to 1), it means there was a replacement, so obviously $aname must be in the array.

---

### Post by jpkotta on 2009-04-20
> **Arndt said:**
> Beware if one of the entries might match the other, for example if you have both "green" and "greenish". Anchoring the grep search (using ^ and $) may be enough to solve that problem.

That's the main reason.  Also, it may or may not be slower to call grep, depending on the size of your array and how often you check for membership.

---

