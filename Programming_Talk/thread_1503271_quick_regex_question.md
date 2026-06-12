---
title: "quick regex question"
date: 2010-06-06
forum: Programming Talk
---

### Post by l3ecl on 2010-06-06
Suppose I have two folders named "Win" and "Lin." Using the find command I would like to search for them by typing: 

```
find . -name (W|L)in
```

but I keep getting the error

```
bash: syntax error near unexpected token `('
```

---

### Post by ju2wheels on 2010-06-06
```

find . -name "[WL]in"

```

---

### Post by trent.josephsen on 2010-06-06
> **ju2wheels said:**
> ```

find . -name "[WL]in"

```

I presume you mean to use -regex, not -name?

Anyway, the better way is the way ju2wheels says, but if you need more than just a character class can offer, put it in single quotes or escape the parentheses with backslashes.  I'm in the habit of putting all regexes of any sort (arguments to egrep, for instance) in single quotes anyway just because there are so many different expansions that could happen without my noticing.  "egrep car{1,5}", for instance, will not grep lines containing car, carr, carrr, carrrr, and carrrrr; it will match lines containing car1 or car5, because of bash's expansion.

---

### Post by l3ecl on 2010-06-06
I tried single quotations using regex but no results came out
```
gg@Ubuntu:~/play$ ls
cap_names  hello_world.sh  Lin  Linux  reg  sname  sorted_names  Win  Windows
gg@Ubuntu:~/play$ find . -regex '[WL]in'
gg@Ubuntu:~/play$ 
```But it works if I use name with double quotes

```
gg@Ubuntu:~/play$ find . -name "[WL]in"
./Win
./Lin
```Howcome in some tutorials they use parenthesis while others use brackets? The tutorial I'm using says (W|L) for the 'or statement' (doesnt work) while [WL] works better. Does anyone know a better way to learn this?

---

### Post by ju2wheels on 2010-06-06
```

find . -regex '.*[WL]in'
find . -regex '.*\(W\|L\)in'

```

Bash isnt the best thing to use if you are just learning how to use regexes in general, due to the need to constantly quote and escape things that you normally wouldnt need to when used in a programming language for example... (unless the book you are reading is on regex as related to bash that is).

---

### Post by l3ecl on 2010-06-06
i'm learning regex mainly for searching in bash anyway. i did not even know other languages used it haha. 

i dont understand howcome the period and asterisk are at the beginning  

```
 find . -regex '.*[WL]in'
```shouldn't the code without asterisk and period work just as effective? (because there are no characters prior to 'W' in the folder named "Windows" or 'L' in the folder named 'Linux') 
 ```
 find . -regex '[WL]in'
```

---

### Post by ju2wheels on 2010-06-06
No they dont work the same.

A single period means to match a single character (.)

So the regex .in would match any 3 letter word ending in "in" at the end.

The asterisk is a form of modifier on the . , meaning to allow it match 0 or more occurrences. Thus when put together, .* means match 0 or more characters (regardless of what they are).

The reason we need .* in this regex is because the find returns the folder path as ./Win or ./Lin instead of Win or Lin , therefore we need to make it ignore the "./" by allowing for any characters before Win or Lin.

Equally the regex could have specifically included those two characters and become \./[WL]in  . We have to escape the . here so that it knows we mean literally match the period and dont take it to mean match any character.

Edit: if you are wondering why -name "[WL]in" worked, taken from the find man page:

> 
 -name pattern
              Base of  file  name  (the  path  with  the  leading  directories
              removed)  matches  shell  pattern  pattern. 


Therefore -name ignores the path (./) appended to the file name so we dont have to explicitly add it to the regex.

---

### Post by l3ecl on 2010-06-06
that was a very informative explanation! very nice attention to detail regarding the ./ return output. thanks for the help =)

---

