---
title: "input errors"
date: 2014-01-23
forum: New to Ubuntu
---

### Post by avdiel1946 on 2014-01-23
feeding this line....
    180 Baltimore Ave. #1
.... into this....
    echo -en "$clrpro Enter STREET ADDRESS -> "; read temp[3]
    if [ ! ${temp[3]} ]; then temp[3]="<unknown>"; fi
    echo -en "\e[14;20H ${temp[3]}"
.... produces this error
/home/larry/bin/addrbook: line 354: [: too many argumentsr expected


feeding this line....
    POB 354
.... into this ....
    echo -en "$clrpro Enter SECOND ADDRESS -> "; read temp[4]
    if [ ! ${temp[4]} ]; then temp[4]="<unknown>"; fi
    echo -en "\e[16;20H ${temp[4]}"
.... produces this ....
home/larry/bin/addrbook: line 359: [: POB: unary operator expected.


later a for loop prints out the inputs correctly.
I am looking for a solution for this, but the only thing I have
found that works is to not leave a space between the numeral and
the previous character. Not real good for readability.
Any suggestions?


thanks....

---

### Post by justleen on 2014-01-23
Can you be a bit more specific as to what your trying to do?
the above code fails when trying to assign values with space into the temp[] array.

 Playing around a bit with the above I found that you can escape the spaces with a \ to make it pass as 1 value.
Somewhere in the last echo its expanding "to much" resulting in the shell trying to execute it.  Try to sanitize the input?

---

