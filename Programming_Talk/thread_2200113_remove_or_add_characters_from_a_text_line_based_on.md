---
title: "remove or add characters from a text line based on a pattern"
date: 2014-01-17
forum: Programming Talk
---

### Post by herbert tamayo on 2014-01-17
Hi, I have a text file with at least 5000 rows, I need to match several kind of patterns such as:

Remove operations:

1. [string]+[number]|[number]|[number]+[symbol], examples: File1=, File14=, File165=
I have been working in these lines:
-this one delete the string File
```

sed -e 's/File//g' input.txt

```

-this one delete all numbers in a line, it doesn't work for me cause I just need to delete the pattern[char][number]|[number]|[number]
```

sed -e 's/[0-9:=]//g' origen

```


2. [String]+[string], examples: Filefile
I don't have any proposals about it at this time


Update Operations:
1. found 2 slashes together, remove them and add this string '/home/data/'
example: 
```

///xy.txt 

```


the output of each matched textline should be:
```

/home/data/xy.txt

```

neither have any proposals at this time.

so, I'm asking you any proposals or comments about the code lines that I have and at least an idea how to match the other patterns where I don't have any advanced .

thank your for your time and help

cheers

---

### Post by TheFu on 2014-01-17
sed -e 's/File[0-9]+=//g' 

sed -e 's#^//#/home/data#go'
This assumes the pattern starts at the beginning of a line. That is handy.

---

### Post by Bucky Ball on 2014-01-17
*Thread moved to **Programming Talk**.*

Unsure why this was in ***Absolute Beginners***. Reduces your chances of help so it is better here.

---

### Post by The Cog on 2014-01-17
The first sed needs extended regex for the + symbol. And the -e isn't really needed for a single expression:
```
sed -r 's/File[0-9]+=//g' input.txt
```

I find # as the separator difficult to read in sed, so I prefer to use | if / is used within the expressions:
```
sed 's|///|/home/data/|g' origen
```

---

