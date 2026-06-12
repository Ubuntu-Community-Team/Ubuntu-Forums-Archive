---
title: "Help with a &quot;Expression&quot; in Bash..."
date: 2010-03-17
forum: Programming Talk
---

### Post by iMisspell on 2010-03-17
I have files with a bunch of lines...

Small example...
```

(ANYTHING IN PARENTHESES DO NOT TOUCH)
(UNTOUCHED TEST!@#TEST1234TEST)
N007T04
N008G54.1P01
N009S1000M03
N010G00X3.97Y7.3
N011G43H02Z0.75
N012Z0.45
N013G1Z0.01F75.M08
N014Y0.F20.
N015G2X3.97Y0.I-3.97J0.F42.5
```

And i need to seperate the line by adding a space between 'letters' and 'numbers' and possibly a 'period' ...
```

(ANYTHING IN PARENTHESES DO NOT TOUCH)
(UNTOUCHED TEST!@#TEST1234TEST)
N007 T04
N008 G54.1 P01
N009 S1000 M03
N010 G00 X3.97 Y7.3
N011 G43 H02 Z0.75
N012 Z0.45
N013 G1 Z0.01 F75. M08
N014 Y0. F20.
N015 G2 X3.97 Y0. I-3.97 J0. F42.5
```


As you will see, im horrible with Regular Expressions, ive tried the following, which is close, but still not working correctly...

```

sed 's/\([0-9]*\)*\([A-Z]\)/\1 \2/g' $file

```

Will produce the following.
The first 'space' before N### can not be there, and the 'spaces' added with-in the parentheses are not wanted.
```

( A N Y T H I N G  I N  P A R E N T H E S E S  D O  N O T  T O U C H)
( U N T O U C H E D  T E S T!@# T E S T1234 T E S T)
 N007 T04
 N008 G54.1 P01
 N009 S1000 M03
 N010 G00 X3.97 Y7.3
 N011 G43 H02 Z0.75
 N012 Z0.45
 N013 G1 Z0.01 F75. M08
 N014 Y0. F20.
 N015 G2 X3.97 Y0. I-3.97 J0. F42.5

```


Any help would be great.


_

---

### Post by Trumpen on 2010-03-17
You just need to add a test for the presence of parentheses in the line:

```
sed '/^[^(]/ s/\([0-9]*\)*\([A-Z]\)/\1 \2/g' $file
```

/^[^(]/ is true if the line doesn't begin with '('

If you want to avoid adding a first space character you may
write:

```
sed '/^[^(]/ s/\([0-9.]\)\([A-Z]\)/\1 \2/g' $file
```

---

### Post by DaithiF on 2010-03-17
slight variation on how to avoid updating lines containing parentheses -- using the '!' negate operator.  
```
sed '/(/!s/\([0-9.]\)\([A-Z]\)/\1 \2/g' testfile
```

---

### Post by iMisspell on 2010-03-17
Thanks to the both of you, its working correctly now.


Am i understanding this correctly...
The following will search the first character of the line, if that character is a 'open parentheses' ( then the expression will skip that line.
> **Trumpen said:**
> ```
sed '/^[^(]/ s/\([0-9.]\)\([A-Z]\)/\1 \2/g' $file
```



And this will search the first character of the line and if that character is not a number or letter, it will skip ?
> **DaithiF said:**
> ```
sed '/(/!s/\([0-9.]\)\([A-Z]\)/\1 \2/g' testfile
```



As for this ???```
'\([0-9.]\)\([A-Z]\)'
```I see you's have removed the wild card form the middle and added a period to the end of the number range, why/how does that work ?



Again, thanks for the help.

_

---

### Post by geirha on 2010-03-17
> **iMisspell said:**
> 
Am i understanding this correctly...
The following will search the first character of the line, if that character is a 'open parentheses' ( then the expression will skip that line.


Yes, or you can say: For all lines that start with any character that is not «(», execute the following sed command.

> **iMisspell said:**
> 
And this will search the first character of the line and if that character is not a number or letter, it will skip ?


«sed '/(/COMMAND'» -> run COMMAND on all lines that match the regex «(».
«sed '/(/!COMMAND'» -> run COMMAND on all lines that does NOT match the regex «(».

And COMMAND in this case is a substitute command (s/regexp/replacement/)

> **iMisspell said:**
> 
As for this ???```
'\([0-9.]\)\([A-Z]\)'
```I see you's have removed the wild card form the middle and added a period to the end of the number range, why/how does that work ?


It matches ONE digit or . (literal punctuation mark, not any char) directly followed by one uppercase letter.

E.g. in «N008G54.1P01» it'll match «8G» and «1P».

---

### Post by iMisspell on 2010-03-18
Thanks geirha
The first one with **/^[^(]/** is alittle confusing for me (i see how its working, but still dont understand why), but the second with the "not" ! made more sence - being '!' is used in other languages.

Anyway... thanks everyone.

_

---

