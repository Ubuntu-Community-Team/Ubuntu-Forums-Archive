---
title: "HELP!! i need some help with this algorithm please!"
date: 2008-01-13
forum: Programming Talk
---

### Post by kishan4910 on 2008-01-13
Read the following algorithm for the recursive procedure called Mystery.

MYSTERY(soFar, toGo)
    length = LEN(toGo)
        IF length = 1 THEN
    PRINT soFar & toGo
        ELSE
           FOR i = 1 to length
        MYSTERY(soFar & MID$ (toGo, i, 1),LEFT$(toGo, i – 1)
                                                                  & RIGHT$(toGo, length – i))
             NEXT i
        ENDIF
END of procedure

Where:
LEN(aSTRING) returns the number of characters in the string held in aString,

MID$(aString, n,m) returns m characters of aString starting at the nth,

LEFT$(aString, n) returns the first n characters of aString,

RIGHT$(aString, n) returns the last n characters of aString,
& joins two strings together (concatenation).

(A) Give the output if the procedure is called by
MYSTERY('' '', ''RED'')

(B) The function is called with
MYSTERY('' '', ''AB'')
Write down all the instructions, including procedure calls, in the order in which they are
executed. You must show the values of the variables in each instruction.

---

### Post by Wybiral on 2008-01-13
Why don't you ask your teacher for help? :)

---

### Post by LaRoza on 2008-01-13
0. We don't do other people's homework
1. Use code or php tags if you post code.

---

### Post by PriceChild on 2008-01-13
Thread Closed.

We are not here do your homework. At least make an attempt at it!

---

