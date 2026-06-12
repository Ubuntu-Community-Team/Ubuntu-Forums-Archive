---
title: "Chmod Explained"
date: 2009-08-29
forum: Outdated Tutorials &amp; Tips
---

### Post by Penguin Guy on 2009-08-29
chmod is an abbreviation of **ch**ange **mod**e. There are two ways to chmod:

_Symbolic (e.g. [COLOR="Green"][FONT="Courier New"]chmod +x[/FONT][/COLOR])_
```

chmod <people><+/-><permissions>
Example: [COLOR="Green"][FONT="Courier New"]chmod o-w[/FONT][/COLOR] (deny others from editing the file)
Example: [COLOR="Green"][FONT="Courier New"]chmod u+rwx[/FONT][/COLOR] (give the owner full control)
Exmaple: [COLOR="Green"][FONT="Courier New"]chmod +rwx[/FONT][/COLOR] (give everyone full control)
Example: [COLOR="Green"][FONT="Courier New"]chmod +x[/FONT][/COLOR] (allow anyone to execute the file)

```
```

_Key:_
r - Read
w - Write
x - Execute

u - The owner of the file
g - The group that the file belongs to
o - Anybody who is not one of the above
a - All users

+ - Add permissions
- - Remove permissions

```


_Numerical (e.g. [COLOR="Green"][FONT="Courier New"]chmod 700[/FONT]_[/COLOR]):
```

                                : The first octet represents permissions for the owner.
        r w x  T                : The second octet represents permissions for the group.
Owner:  4 2 1  7                : The third octet represents permissions for everyone else.
Group:  0 0 0  0                : For each octet, start at 0 and:
Other:  0 0 0  0                : +4 for read permission.
                                : +2 for write permission.
Command: [COLOR="Green"][FONT="Courier New"]chmod 700[/FONT][/COLOR]              : +1 for execute permission.

```

[What is an octet?]("http://ubuntuforums.org/showpost.php?postid=7891167") [What Happened to +3?]("http://ubuntuforums.org/showpost.php?p=7891167")
Read more: [[COLOR="Blue"]Wikipedia[/COLOR]]("http://en.wikipedia.org/wiki/Chmod"). [[COLOR="Blue"]Man page[/COLOR]]("http://ss64.com/bash/chmod.html").

---

### Post by Penguin Guy on 2009-09-01
When I refer to 'octets' in my chmod guide, I am referring to these:
[FONT="Courier New"][COLOR="Green"]chmod **644** file[/COLOR][/FONT]

While digits go from 0-9, octets go from 0-7 (skipping 8 and 9). A number written using digits is called a decimal, a number written using octets is called an octal.
```
Counting to 20 in Decimal: 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20 
Counting to 20 in Octal: 1, 2, 3, 4, 5, 6, 7, 10, 11, 12, 13, 14, 15, 16, 17, 20, 21, 22, 23, 24
```

---

### Post by credobyte on 2009-09-01
Might be a little bit offtopic, but .. does anyone have an answer to the following question ?

> Why there's no +3 ( +1, +2 ... +4 ) ?

---

### Post by dondad on 2009-09-01
> **credobyte said:**
> Might be a little bit offtopic, but .. does anyone have an answer to the following question ?

Look at the place values. The first (rightmost) digit is the ones, the next is the 2's and the next is the 4's. To make 3 you would use the ones and the 2's place. so:
1 is 001
2 is 010
3 is 011
4 is 100
5 is 101
6 is 110
7 is 111.

There is no one place for the 3's

This is analogous to the base 10 system with the first place being the ones, the next the 10's etc.

---

### Post by Penguin Guy on 2009-09-03
> **credobyte said:**
> Might be a little bit offtopic, but .. does anyone have an answer to the following question ?

> Why there's no +3 ( +1, +2 ... +4 ) ?

Good question! The answer is simple; +3 is switched with +4 to avoid a duplicate number 3 in the sum octet:
```

_+4 System_      _+3 System_
**r w x  &#931;       r w x  &#931;**
4 2 1  7       3 2 1  6
4 2 0  6       3 2 0  5
4 0 1  5       3 0 1  4
4 0 0  4       3 0 0  [COLOR="Red"]3[/COLOR]
0 2 1  3       0 2 1  [COLOR="Red"]3[/COLOR]
0 2 0  2       0 2 0  2
0 0 1  1       0 0 1  1
0 0 0  0       0 0 0  0

```

Although this may seem confusing, it makes sense mathematically. This kind of code is based off binary.

---

### Post by Fatjoint on 2009-09-03
This is a subject of it's own, but here's a quick primer on counting in other number systems.

Counting in any base system is exactly the same as counting in decimal - representing, or writing down the count is what is different.

```

Base10 (Decimal) 1,110 has the following meaning:

10^3 10^2 10^1 10^0
------------------- = (1*10^3)+(1*10^2)+(1*10^1)+(0*10^0)
1    1    1    0


Base8 (Octal) 5477 has the following meaning:

8^3 8^2 8^1 8^0
--------------- = (5*8^3)+(4*8^2)+(7*8^1)+(7*8^0)
5   4   7   7


Base30 (Trigesimal) 11T has the following meaning:

30^2 30^1 30^0 
------------------- = (1*30^2)+(1*30^1)+(30*30^0)
1    1    T  (T represents 30)

```

How do we write these numbers?  Each position has a representitive character or symbol whose count is equal to N(max)-1.  

In Base8 (Octal), each position is counted from 0 (meaning none) to 7 (the maximum count in that position).  When we want to say that we've counted past 7, we add an octet position and start counting again in the base^0 position again.

In Base10, we count from 0 to 9.  When we want to say that we've counted past 9, we add a deimal position and start counting again in the base^0 position again.

In Base30, we count from 0 to T.  When we want to say that we've counted past 30, we add a trigesimal position and start counting again in the base^0 position again.

Counting in a base 3 system would look like this:

```

3^3 3^2 3^1 3^0
---------------
1   1   1   1   = 40
    3   3   3   = 39
    3   3   2   = 38
    3   3   1   = 37
    3   2   3   = 36
    3   2   2   = 35
    3   2   1   = 34
    3   1   3   = 33
    3   1   2   = 32
    3   1   1   = 31
    2   3   3   = 30

....

....

    0   0   0   = 0

```

---

