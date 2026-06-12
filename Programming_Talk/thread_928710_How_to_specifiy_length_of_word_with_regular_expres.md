---
title: "How to specifiy length of word with regular expressions"
date: 2008-09-24
forum: Programming Talk
---

### Post by flummoxed on 2008-09-24
Hello,

I'm writing a script that searches through words using grep and regular expressions. It's looking for words that are at least 10 characters long, and that can be typed using only certain characters... I'm not sure exactly how to make it so that it only returns words that are least 10 characters. I was thinking something along the lines of:

```

grep [asghdg]......... file

``` 

That works for getting words with that many chracters, but it matches ANY character, not just the ones specified in brackets. I'm looking for a regular expression that will define how long the word is. I'm just lookin for a kick in the right direction.

Thanks

---

### Post by ghostdog74 on 2008-09-24
the words in square brackets is called a range. show a sample file, and describe what you want to get as final output.

---

### Post by flummoxed on 2008-09-24
Sample file:

```

exaggerate
dog
candy 
party

```

Desired output:

```
exaggerate
```

---

### Post by ghostdog74 on 2008-09-24
```

awk '
{
 flag=0
 for( i=1;i<=NF;i++){
  m=split($i,temp,"")
  for(o=1;o<=m;o++){
    if ( temp[o] !~  /[asdfgqwertzxcvb]/) {
      flag=1
      break
    }
  }
  if (!flag) {
   print $i
  }
 }
}
' file

```
output
```

# ./testnew.sh
exaggerate


```

or using egrep
```

egrep -w '[asdfgqwertzxcvb]+' file

```

---

### Post by eentonig on 2008-09-24
install and try **txt2regex**. It's a CLI tool that guides you through the process of forming a REGEX for a variety of environments (vi, php, perl, bash,...)

I wouldn't use it to create long and complex regexp statements, but for finding the correct syntax in a case like this, it will do.

---

### Post by stylishpants on 2008-09-24
You want repetition specification.

Find the documentation here:
```

man egrep | less -p Repetition

```

Note that basic grep doesn't support this, you need to use egrep (or switch over to perl-compatible regexps with pcregrep or a simple perl one-liner.)

Here's an example:
```
fhanson@fhanson:/tmp$ cat file
exaggerate
exaggerates
awordthatisthirtyfivecharacterslong
dog
candy 
party

### Print words that are exactly 10 chars long
fhanson@fhanson:/tmp$ egrep '^[A-Za-z]{10,10}$' test
exaggerate

### Print words that are between 10 and 15 chars long
fhanson@fhanson:/tmp$ egrep '^[A-Za-z]{10,15}$' test
exaggerate
exaggerates

### Print words that are 10 or more chars long
fhanson@fhanson:/tmp$ egrep '^[A-Za-z]{10,}$' test
exaggerate
exaggerates
awordthatisthirtyfivecharacterslong

```

---

### Post by flummoxed on 2008-10-01
Thanks for the tip, the txt2regex tool is a great help.

---

### Post by Mindzai on 2008-10-01
txt2regex is brilliant, thanks for the heads up.

---

### Post by thesoothsayer on 2008-10-01
> **eentonig said:**
> install and try **txt2regex**. It's a CLI tool that guides you through the process of forming a REGEX for a variety of environments (vi, php, perl, bash,...)

I wouldn't use it to create long and complex regexp statements, but for finding the correct syntax in a case like this, it will do.
Great tool. Thanks.

Would be great if there's a tool that would take in a regex from one language/tool and convert it to another. Drives me up the wall sometimes when a seemingly simple query that works in one language completely fails in another and I have to spend time looking up the differences. Would be worth doing so if I use them often enough but since I only use them sporadically, I'll forget the differences by the next time I use them.

---

