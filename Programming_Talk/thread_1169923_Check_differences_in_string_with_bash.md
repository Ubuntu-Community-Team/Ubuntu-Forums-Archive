---
title: "Check differences in string with bash"
date: 2009-05-25
forum: Programming Talk
---

### Post by wesg on 2009-05-25
Part of a script I'm writing involves combining files that have parts a and b. To find those files, I need to compare two strings and check if the only difference is a single character (A is B, or 1 is 2, for example).

What command can I use to do this and how might it be executed?

---

### Post by soltanis on 2009-05-25
Most UNIX utilities operate on files, not strings. I know wc could count the number of chars in a file, and diff could tell you whether two files differ, but other than that I'm not sure there is a utility already written for doing this (there probably is, I just don't know it).

---

### Post by ghostdog74 on 2009-05-25
why don't you explain what you want to do with examples?

---

### Post by wesg on 2009-05-25
I want to compare strings and find out if they are only different by 1 letter. I found the solution though, so it's all good.

However, I did have another question... how can I compare 2 arrays? I'm looking for a file that just added to the directory (take a snapshot before, then compare it to the after and find the new file). I've tried ls -t and that works mostly, but unfortunately some of the files I've unrar-ed were created years ago, and that throws the listing off.

---

### Post by k2t0f12d on 2009-05-26
> **wesg said:**
> However, I did have another question... how can I compare 2 arrays?

```
#!/bin/bash

## FILE cmp-array.sh
#
# compares the contents of two arrays
# exit 0 if arrays are identical
# exit with error status if arrays are not identical
#
## USAGE: cmp-array.sh <array1> <array2>
#
# NOTE: arrays must undergo shell expansion during processing
#       to invoke this command properly each array should be typed thusly;
#
#       cmp-array.sh "${array1[@]}" "${array2[@]}"
#
#       where array1 and array2 are replaced by the actual array name
#
## RETURNS
#
#       0       success
#       1       error
#
## REQUIRES
#
#       n/a
#

array1=( "$1" )
array2=( "$2" )

# error if either array is empty
test "${array1[@]}" || exit 1
test "${array2[@]}" || exit 1

# error if both arrays do not have the some num of elements
test "${#array1[@]}" = "${#array2[@]}" || exit 1

index=0
while test "$index" -le "${#array1[@]}"; do

  if test "${array1[$index]}" = "${array2[$index]}"; then
        (( index +=1 ))
        continue
  else
        exit 1
  fi

done

exit 0

#
## END FILE cmp-array.sh
```

---

