---
title: "sed regex issue and special characters"
date: 2010-08-28
forum: Programming Talk
---

### Post by wannabegeek on 2010-08-28
hi all

I am going crazy trying to figure this out...I am still fairly new to scripting and generally program only math stuff....

I need to search through all files in a directory with *.tex and replace  '*' with 
`*'   
EXAMPLE:  'hard work'  --->  `hard work'

here's what I thought would work:
```

sed -i 's/\'[Aa-Zz]\'/\`[Aa-Zz]\'/g' 

```I get an error, unterminated `s' command...goggle was not helpful....

to test. I ,made a simpler replacement expression.
```

sed -i 's/\'[a-z]\'//g' file1.tex

```still no good...I am not entirely sure that [Aa-Zz] is right either, gonna search for that now that I think about it...

TIA,
wbg

---

### Post by amauk on 2010-08-28
```
sed "s|'\(.*\)'|\`\1'|"
```

---

### Post by Dayofswords on 2010-08-28
> **wannabegeek said:**
> 
still no good...I am not entirely sure that [Aa-Zz] is right either, gonna search for that now that I think about it...
not sure if thats the problem, but i think you have to do it [A-Za-z]

---

### Post by wannabegeek on 2010-08-28
@amauk
thanks for reply...your code did not work. The terminal went black for while until I killed the process.

I tried:
```

 sed -i s/\'[A-Za-Z]\'//g  file2.tex

```

no luck...adding '  around the regexp get me back to a weird problem where I get the >
and hit another '   and the error comes back,   unknown option to `s'

---

### Post by amauk on 2010-08-28
> **wannabegeek said:**
> @amauk
thanks for reply...your code did not work. The terminal went black for while until I killed the process.:confused: you sure you copied it right?

```
tony@tony-desktop:~$ echo "'foo'" | sed "s|'\(.*\)'|\`\1'|"
`foo'
```

---

### Post by wannabegeek on 2010-08-28
oh it does work !  I used it wrong...

I don't understand the command tho ....it looks really different from what I thought sed
syntax looked like...

---

### Post by apmcd47 on 2010-08-28
*'[Aa-Zz]* is grouping the range a-Z which is your problem as the ASCII character set, upon which the one you are using is based, has values 65-90 for *A-Z* and 97-122 for *a-z*, so sed is failing to interpret the range. Try instead *[A-Za-z]* which groups the two ranges *A-Z* and *a-z*. Alternatively some people would say you should be using *[:alpha:]* which uses the alphabetic character class in your character set.

Your second problem is you are effectively putting a wildcard on both sides of the expression. Try instead:
```
sed -i 's/\'\([:alpha:]\)\'/\`\1\'/g' file1.tex
```
The bit in the parentheses is then substituted in the right hand side of the expression whenever the \1 is met. A second grouping in parentheses would substitute \2 and so on.

Andrew

---

### Post by amauk on 2010-08-28
> **wannabegeek said:**
> I don't understand the command tho ....it looks really different from what I thought sed
syntax looked like...
It just reads,
match a single quote, plus any character any amount of times, plus a single quote and replace with a backtick, plus the previously matched stuff, plus a single quote

The "any character any amount of times" is wrapped in parentheses, so we can use the matched values in the replacement section
the \1 is the matched value

If you're matching single quotes, then it's just easier to bound the expression in double quotes (and vice-versa) - just saves escaping things

I tend to use the pipe character (|) to delimit sed
(I use sed a lot with paths, so having slash as the delimiter makes little sense)

so the end result is
```
sed "s|'\(.*\)'|\`\1'|"
```

---

### Post by wannabegeek on 2010-08-28
awesome...both expert codes 

i kinda understand now...() is used to tell shell to evaluate within () first but also needs escape characters around ( and )....the replace part uses  \1  which I saw in man but didn't know what it meant...

gonna stare at code for a while longer...its really neato

thanks a ton to amauk, Days and apmcd47

---

### Post by ghostdog74 on 2010-08-29
all bash
```

#!/bin/bash
shopt -s nullglob
for file in *.tex
do
   if [ -f "$file" ];then
       exec 4<"$file"
       while read -r line<&4
       do
           case "$line" in
             *"*"*)
                line="${line//\*/\`*}";;
           esac
           echo "$line"
       done >t
       exec 4<&-
       mv t "$file"
   fi
done


```

---

