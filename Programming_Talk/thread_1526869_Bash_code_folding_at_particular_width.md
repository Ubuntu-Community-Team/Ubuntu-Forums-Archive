---
title: "Bash code folding at particular width"
date: 2010-07-08
forum: Programming Talk
---

### Post by vamega on 2010-07-08
[FONT=Garamond]Hi.

I'm trying to find a way to fold code at a width of 75 columns.
Should any line of code be longer than 75 columns, the rest of the line should be moved the the next line and prefixed with a [/FONT]&#8618; character.

Any ideas on how this could be done.
I have looked at the fold and fmt commands, but I don't think they do what I expect them to do.

Thanks

Vamega

---

### Post by dwhitney67 on 2010-07-08
For grins, I practiced my awful bash skills and came up with two alternatives, neither of which includes that special character you want.

```

!/bin/bash

SENTENCE="This is hopefully a long sentence that contains sufficient characters to exceed the max line width of 75 chars."

# Style 1
if [ ${#SENTENCE} -gt 75 ]
then
        echo ${SENTENCE:0:75}
        echo ${SENTENCE:75}
else
        echo ${SENTENCE}
fi


# Style 2
declare -i n
declare -i len

n=0
IFS=" "

for word in $SENTENCE
do
        len=$n+${#word}

        if [ $len -gt 75 ]
        then
                echo ""
                n=${#word}+1
        else
                n=$n+${#word}+1
        fi

        echo -n "$word "
done
echo
unset IFS

```

---

### Post by DaithiF on 2010-07-08
Hi,
Not sure about that continuation character -- I don't think its part of the ascii set.  Heres an example using sed that puts in a different character that is at least ascii:

```
sed -r 's/^.{75}/&\n\xBB/' somefile

```

---

