---
title: "MySQL unsigned BIGINT issues"
date: 2013-10-21
forum: Programming Talk
---

### Post by ICanHasNick on 2013-10-21
Hi folks,

in the mysql-client the SQL Query: "SELECT 0xFFFFFFFFFFFFFFFF + 0;"   // 64 bit number
gives the following response from my MySQL server:

[FONT=courier new]+------------------------+[/FONT]
[FONT=courier new]| 0xffffffffffffffff + 0 |[/FONT]
[FONT=courier new]+------------------------+[/FONT]
[FONT=courier new]|   18446744073709552000   |[/FONT]
[FONT=courier new]+------------------------+[/FONT]

which is quite close but not close enough.

The exact value (for an unsigned BIGINT) is:  18446744073709551615

Actually, I can't use almost any 64 bit hex string for calculations or bit shift operations.
(if not explicitly casting it with "CAST( 0xffffffffffffffff AS UNSIGNED)" to an unsigned BIGINT, which works).

With 32 bit hex strings however I didn't experience this problems (though I did not test all of them :)).

can anyone reproduce this behaviour on his/her machine? 

my params:

uname -a:    Linux laptop 3.2.0-39-generic#62-Ubuntu SMP Thu Feb 28 00:28:53 UTC 2013 x86_64 x86_64 x86_64GNU/Linux
mysql --version: Ver 14.14 Distrib 5.5.32, fordebian-linux-gnu (x86_64) using readline 6.2

regards

---

### Post by Bachstelze on 2013-10-21
The value you are trying to use is outside the range of type BIGINT. I don't know what MySQL is supposed to do in that case, but in C, when you try to store an out-of-range value in a signed type, the result is undefined. It could be that MySQL just stores the value "as is" in a C int64_t, which would explain what you get.

If you want to store a hex string, and not a numeric value, you should use UNSIGNED BIGINT.

---

### Post by ICanHasNick on 2013-10-22
I know that mixing of signed and unsigned values requires some attention from the programmers side.

But in this case, the MySql server just doesn't do what it is supposed to do.


According to the manual of the 5.5 Server:


> 


12.6.1. Arithmetic Operators
…
The usual arithmetic operators are available. The result is determined according to the following rules:
In the case of -, +, and *, the result is calculated with BIGINT (64-bit) precision if both operands are integers.
[COLOR=#ff8c00]If both operands are integers and any of them are unsigned, the result is an unsigned integer[/COLOR]. For subtraction, if the NO_UNSIGNED_SUBTRACTION SQL mode is enabled, the result is signed even if any operand is unsigned.
If any of the operands of a +, -, /, *,% is a real or string value, the precision of the result is the precision of the operand with the maximum precision.



the calculation mistake when using the hex representation of numbers is easily proved.

[FONT=Tlwg Typist]mysql>SELECT 9223372036854775807 + 1; [/FONT][FONT=Tlwg Typist]<-- [/FONT][FONT=Tlwg Typist]biggest unsigned BIGINT + 1[/FONT]
[FONT=Tlwg Typist]ERROR 1690(22003): BIGINT value is out of range in '(9223372036854775807 +1)'            <-- CORRECT[/FONT]


[FONT=Tlwg Typist]mysql>SELECT 0x7fffffffffffffff + 1;  [/FONT][FONT=Tlwg Typist]<-- [/FONT][FONT=Tlwg Typist]the same in hex[/FONT]


[FONT=Tlwg Typist]+------------------------+[/FONT]
[FONT=Tlwg Typist]|0x7FFFFFFFFFFFFFFF + 1  |[/FONT]
[FONT=Tlwg Typist]+------------------------+[/FONT]
[FONT=Tlwg Typist]|   9223372036854776000    |    <-- WRONG[/FONT]
[FONT=Tlwg Typist]+------------------------+[/FONT]


Now before I fill out a bug report, I just would like to know, whether this affects 
only my system or if others can reproduce the observed problem as well.


Regards

---

### Post by Bachstelze on 2013-10-22
Well then I have the same behavior on two machines (one Debian and one Ubuntu, both MySQL 5.5).

---

### Post by ICanHasNick on 2013-10-22
Thanks for confirming!

---

### Post by trent.josephsen on 2013-10-22
I don't think you've demonstrated that this is a bug.

The manual section you quote only applies when both operands are unsigned. 0xFFFFFFFFFFFFFFFF is a string, so it is automatically converted to a number when used in a numeric expression -- but the [manual](https://dev.mysql.com/doc/refman/5.5/en/type-conversion.html) is not clear on what kind of "number" it becomes. The assumption that it is unsigned is unwarranted IMO.

If the list of rules on the aforelinked page can be assumed to apply to arithmetic operations as well as comparisons, then 0xFFFFFFFFFFFFFFFF is converted to a floating-point number first, which could explain the loss of precision.

---

### Post by trent.josephsen on 2013-10-22
Wait -- I said "0xFFFFFFFFFFFFFFFF is a string" but that's not necessarily correct; I skipped some reasoning. [This page](https://dev.mysql.com/doc/refman/5.5/en/hexadecimal-literals.html) says that hexadecimal literals, in numeric contexts, act like integers with 64-bit precision. It does not specify signedness. Perhaps 0xFFFFFFFFFFFFFFFF doesn't make sense as a numeric literal, since its "numeric value" is greater than a 64-bit signed value can hold, and so it falls back to the string rule. At least, that's what I was thinking when I wrote the previous post.

---

### Post by donsy on 2013-10-22
```
Server version: 5.5.30-cll MySQL Community Server (GPL)

Copyright (c) 2000, 2013, Oracle and/or its affiliates. All rights reserved.

Oracle is a registered trademark of Oracle Corporation and/or its
affiliates. Other names may be trademarks of their respective
owners.

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> select 0x7FFFFFFFFFFFFFFF +0;
+-----------------------+
| 0x7FFFFFFFFFFFFFFF +0 |
+-----------------------+
|   9223372036854776000 |
+-----------------------+
1 row in set (0.00 sec)

mysql> select 0x7FFFFFFFFFFFFFFE +0;
+-----------------------+
| 0x7FFFFFFFFFFFFFFE +0 |
+-----------------------+
|   9223372036854776000 |
+-----------------------+
1 row in set (0.00 sec)

mysql> select 0x7FFFFFFFFFFFFFFD +0;
+-----------------------+
| 0x7FFFFFFFFFFFFFFD +0 |
+-----------------------+
|   9223372036854776000 |
+-----------------------+
1 row in set (0.00 sec)


```

---

### Post by ICanHasNick on 2013-10-25
> **trent.josephsen said:**
> ... Perhaps 0xFFFFFFFFFFFFFFFF doesn't make sense as a numeric literal, since its "numeric value" is greater than a 64-bit signed value can hold...

[FONT=Ubuntu Mono]
[/FONT][SIZE=3][FONT=Ubuntu Mono]I suppose we agree, that you can't see on the outside of any hex-literal whether it denotes a signed or unsigned integer. 
Thus each program has to make an educated guess how to interpret the received value. [/FONT][/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3][FONT=Ubuntu Mono]The mysql-client for instance never interprets hex-literals inside querys as signed; even not in the case when they should 
be inserted into a column holding signed integers (which is just another annoyance).[/FONT][/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3][FONT=Ubuntu Mono]The observed bug is something else.[/FONT][/SIZE]

[SIZE=3][FONT=Ubuntu Mono]There is acertain threshold (0x002000000000000E or 9007199254741006)[/FONT][/SIZE]
[SIZE=3][FONT=Ubuntu Mono]from whereon things start being buggy.[/FONT][/SIZE]
[SIZE=3]
[/SIZE][SIZE=3][FONT=Ubuntu Mono]m[FONT=courier new]ysql>SELECT 0x002000000000000E+0;[/FONT][/FONT][/SIZE][FONT=courier new]
[SIZE=3]+----------------------+[/SIZE]
[SIZE=3]|0x002000000000000E+0  |[/SIZE]
[SIZE=3]+----------------------+[/SIZE]
[SIZE=3]|    9007199254741006     | <-- STILL GOOD[/SIZE]
[SIZE=3]+----------------------+[/SIZE]
[SIZE=3]1 row in set(0.00 sec)[/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3]mysql>SELECT 0x002000000000000E+1;[/SIZE]
[SIZE=3]+----------------------+[/SIZE]
[SIZE=3]|0x002000000000000E+1  |[/SIZE]
[SIZE=3]+----------------------+[/SIZE]
[SIZE=3]|    9007199254741008     | <-- BROKEN FROM HERE ON[/SIZE]
[SIZE=3]+----------------------+[/SIZE]
[SIZE=3]1 row in set(0.00 sec)[/SIZE]
[/FONT][SIZE=3]
[/SIZE]
[SIZE=3][FONT=Ubuntu Mono]In the next days I will report the bug to Oracle directly and see what they have to say about it.[/FONT][/SIZE]
[SIZE=3]
[/SIZE]
[SIZE=3][FONT=Ubuntu Mono]Regards[/FONT][/SIZE]

---

### Post by trent.josephsen on 2013-10-25
That's consistent with IEEE 754's double (a standard for floating-point numbers), which has 53 bits of precision in the mantissa.

I'm not saying it's not weird, I'm just saying it's not necessarily a bug. [This page](https://dev.mysql.com/doc/refman/5.5/en/hexadecimal-literals.html) says that hex values act like integers (64-bit precision) in numeric contexts, but it doesn't specify the semantics for the conversion that must take place. It's not what I would expect, but that very page does warn you to use CAST(... AS UNSIGNED) if you want to always treat a hex string as an unsigned number, which you've already said works.

[The manual also says](https://dev.mysql.com/doc/refman/5.5/en/cast-functions.html) that "[i]f you use a string in an arithmetic operation, it is converted to a floating-point number during expression evaluation." That would seem to be the rule you're running into. It's a bit weird in light of the act-like-integers rule, but I can see why someone might do things this way.

Weird? Yes. Poorly documented? Definitely. Buggy? That remains to be seen.

---

### Post by ICanHasNick on 2013-10-25
Yes, you are right, the hex-literals are converted to a double value and from the 53rd bit on all the precision is lost.
Considering the bug dillema everything boils now down to the question "What is a numerical context"

from the manual we read:
"in numeric contexts, hexadecimal values act like integers (64-bit precision)."

if 0xFFFFFFFFFFFFFFFF + 0 is not a numeric context than I would like to see an example of any valid numeric contex where hex literals are treated like 64-bit integers.
Anyway, be it a bug or not, I am happy I hadn't to find it out the hard way - after an application has arrived at the customer. :)
This bears so much potential for broken applications that it should be fixed anyway.

---

### Post by trent.josephsen on 2013-10-25
But it *does* behave like an integer -- if it didn't, it would have printed as something like 1.84467440737096e+19 or however exactly MySQL normally formats floating-point numbers. It's just not the integer you expect.

It could be, for instance, that the strings-always-floating-point rule is a rule of standard SQL, but implicitly converting hex strings to integers is a MySQL-specific extension, in which case this is the intended behavior and it can't change without breaking standards compliance. If there's not a good reason for it, I would expect the devs to agree that it needs to be changed, so by all means submit a bug report.

---

