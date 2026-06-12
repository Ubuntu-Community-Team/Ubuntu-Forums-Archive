---
title: "new to REGEX"
date: 2013-07-01
forum: Programming Talk
---

### Post by jairoh_ on 2013-07-01
i tried matching this postal codes 
A9A 9A9
B3Z 2W3
C8D 2K3
A9A 9A9



my first regex that works fine is 
```

^[A-Z]\d[A-Z] \d[A-Z]\d$

```



and this second regex only matches [B]A9A 9A9
[/B]```

^([A-Z])(\d)\1 \2\1\2$

```

anyone can explane? im actually using regexpal. tnx

---

### Post by trent.josephsen on 2013-07-01
What else did you expect it should match? What were you hoping it would do when you wrote it?

---

### Post by Vaphell on 2013-07-01
i guess he thought that \1 and \2 work as a shorthand for the subexpression defined earlier, eg ([a-z])([0-9])\1\2 => [a-z][0-9][a-z][0-9], not the exact value matched.

OP, A9A 9A9 works because [A-Z] matches A and sets it as the value of \1, \d matches 9 and sets it as the value of \2, then you get further, to \1's and \2's which demand these established values, obviously A=A and 9=9 (A9A 9A9), but B!=Z and B!=W and 3!=2 (B3Z 2W3)

---

### Post by jairoh_ on 2013-07-01
> **Vaphell said:**
> i guess he thought that \1 and \2 work as a shorthand for the subexpression defined earlier, eg ([a-z])([0-9])\1\2 => [a-z][0-9][a-z][0-9], not the exact value matched.

OP, A9A 9A9 works because [A-Z] matches A and sets it as the value of \1, \d matches 9 and sets it as the value of \2, then you get further, to \1's and \2's which demand these established values, obviously A=A and 9=9 (A9A 9A9), but B!=Z and B!=W and 3!=2 (B3Z 2W3)
now i understand. so that means it captures the value and not the expression, right? thank you sir.

---

### Post by d347hm4n on 2013-07-05
[SIZE=2]The valid UK postcode regex is as follows:

^([A-PR-UWYZ0-9][A-HK-Y0-9][AEHMNPRTVXY0-9]?[ABEHMNPRVWXY0-9]? {1,2}[0-9][ABD-HJLN-UW-Z]{2}|GIR 0AA)$

Regular expression to match valid UK postcodes. In the UK postal system not all letters are used in all positions (the same with vehicle registration plates) and there are various rules to govern this. This regex takes into account those rules. Details of the rules: First half of postcode Valid formats [A-Z][A-Z][0-9][A-Z] [A-Z][A-Z][0-9][0-9] [A-Z][0-9][0-9] [A-Z][A-Z][0-9] [A-Z][A-Z][A-Z] [A-Z][0-9][A-Z] [A-Z][0-9] Exceptions Position - First. Contraint - QVX not used Position - Second. Contraint - IJZ not used except in GIR 0AA Position - Third. Constraint - AEHMNPRTVXY only used Position - Forth. Contraint - ABEHMNPRVWXY Second half of postcode Valid formats [0-9][A-Z][A-Z] Exceptions Position - Second and Third. Contraint - CIKMOV not used

[/SIZE][SIZE=2]Matches: 
DN3 6GB | SW42 4RG | GIR 0AA
Non-Matches: 
SEW4 5TY | AA2C 4FG | AA2 4CV[/SIZE][SIZE=2]


Taken unashamedly from: [/SIZE][http://regexlib.com/REDetails.aspx?regexp_id=260](http://regexlib.com/REDetails.aspx?regexp_id=260)[SIZE=2]
[/SIZE][COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]

---

