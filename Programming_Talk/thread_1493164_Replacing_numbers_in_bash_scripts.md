---
title: "Replacing numbers in bash scripts"
date: 2010-05-25
forum: Programming Talk
---

### Post by bluesmodular on 2010-05-25
Hi,

I have lines in some files that look exactly as below, and the line numbers they occur in are always the same. (Lines 136-139)

W 0.00000000 0.00000000 2.00000000
W 0.50000000 0.50000000 2.50000000
W 0.00000000 0.00000000 3.00000000
W 0.50000000 0.50000000 3.50000000

I'd like to replace the last number in each row for each file by numbers related to the variable $vacheight, so that the median of these 4 numbers is always half of $vacheight.

The files are all named "run_example", but are in different folders named "examples#" where # is a number from 140 to 199.

As a related example, Line 117 reads:
```

  celldm(3)   = 5.000,

```Below is the relevant section of code that works for Line 117 and increments the number on Line 117 by 0.1 each time, in a different folder.

```

vacheight=`expr 4.500`
for i in */run_example; do
    printf '117s/= [^,]*/= %s/\nwq\n' "$vacheight" | ed -s "$i"
    vacheight=$(echo "scale=3; $vacheight + 0.100" | bc)
done

```Thank you very much for your help!

---

### Post by DaithiF on 2010-05-26
Hi,
I'm not clear whether you're asking for help with:
(a) a maths question of how these 4 numbers need to change to still be the median of another number (or half of another number) as that number changes, or
(b) the technical question of how to replace these numbers in the file

For (a), aren't there an infinite set of numbers whose median would be another number.  I think you need to give more detail there.

by the way, the printf / ed combination is a little crazy, why not just use sed.
```
sed -i "117s/[0-9.]\+,$/$vacheight,/" somefile
```

---

