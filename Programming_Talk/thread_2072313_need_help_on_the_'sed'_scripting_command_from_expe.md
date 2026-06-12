---
title: "need help on the 'sed' scripting command from expert"
date: 2012-10-17
forum: Programming Talk
---

### Post by s1baker on 2012-10-17
hi,

I have used the cat command to combine several files, like this:
```
cat file1 file2 file3 > file4
```
then, I used the sort command on file4.
 
let's say for example that file4 now looks like this:
```
 
   1   a
1 A
     2 b
 #  comment here
2 B

3  c
# more comments here
3 c


(and so on )

```

question:
How can I use the sed cammand to: 
1) take out all the blank lines
2) take out any line that the first non-blank character is a '#' ( otherwords, remove the comments )
3) make all the text lower case ( or upper case, don't matter)
4) take out all blanks from the start of all lines
5) put exactly same number of blanks ( say 6 for example ) between the first text in a line and the second text in that same line.

otherwords, so file4 will now look like this:
```

1      a
1      a
2      b
2      b
3      c
3      c

```
 
I want it like this so I can do a uniq ( unique command, I think the name is 'uniq' )

so that file4 in it's final form will look like this:
```

1      a
2      b
3      c

```


thanks

---

### Post by Lars Noodén on 2012-10-17
```

sed -e '/^[[:space:]]*#/d;/^[[:space:]]*$/d;s/^[[:space:]]*//;s/[[:space:]][[:space:]]*/      /g' file4

```

You can read is by looking at the distinct segments between the semicolons.  

The first deletes the comments.  
/^[[:space:]]*#/d

The second deletes the blank lines.
/^[[:space:]]*$/d

The third deletes leading whitespace
s/^[[:space:]]*//

The last one normalizes the number of white space.
s/[[:space:]][[:space:]]*/      /g

That last one is not so perfect and will be off a little when the data in the columns is wider or narrower because the number of spaces will always be the same regardless of the width.

---

### Post by papibe on 2012-10-17
Hi s1baker.

If you are not committed to do the work on sed, you can easily get your result using 'awk':
```
awk '{if (!((NF == 0) || ($1 == "#"))) print $1, $2}' input_file.txt
```
Let us know how it goes.
Regards.

---

### Post by s1baker on 2012-10-17
both of these work fine, but I get this:

```

1      a
1      A
2      b
2      B
3      c
3      c

```

Otherwords, I get a lc '1      a' and a uc '1      A'

How would I then do a unique command so I would wind up with something like this:
```

1      a
2      b
3      c

```

---

### Post by Vaphell on 2012-10-17
in awk use tolower($2) instead of $2
in sed 's/.*/\L&/'

---

### Post by s1baker on 2012-10-17
tremendous guys.

I did
```

uniq file4 to file_final

```

and got this for file_final
```

1 a
2 b
3 c

```

Amazing that this can all be put on one line.
I have programmed quite a bit in the old MS Qbasic and some in C, and stuff like this I always had to read a file in line by line, and parse the line.
Took quite a few lines of code.

Thanks again.

---

### Post by Lars Noodén on 2012-10-17
Or use the -f option if you are using [sort](http://manpages.ubuntu.com/manpages/precise/en/man1/sort.1posix.html).

```

awk '{if (!((NF == 0) || ($1 == "#"))) print $1, $2}' input_file.txt | sort -uf > output.txt

```

---

### Post by s1baker on 2012-10-17
supose I wanted to make a script file where all of this would be in a executable script.

Lets say that I would have a directory that one time might have ```
 file1 file2 
```
in it and another time it might have a different number of files in it ```
 file1 file2 file3
```


so I would have my script read a list?
otherwords, how would I tell my script to loop the cat command to read in a variable number of files.

```

cat (somehow list the files here) > filex

awk '{if (!((NF == 0) || ($1 == "#"))) print $1, tolower($2)}' filex | sort -uf > file_final

```

---

### Post by Lars Noodén on 2012-10-17
[Globbing](http://manpages.ubuntu.com/manpages/precise/en/man7/glob.7.html) should work if the files have some part of the name in common.

```

cat file* > filex
cat *.txt > filex

```

etc.

---

### Post by s1baker on 2012-10-17
Excellent. You guys are the greatest.

All my files will be named file(1-x)
so I will have this to paste into the terminal:

```

cat file* > filex & 
awk '{if (!((NF == 0) || ($1 == "#"))) print $1, tolower($2)}' filex | sort -uf > file_final

```

---

### Post by papibe on 2012-10-17
In this case, I would not recommend using the '&' at the end of the 'cat', since you need to wait for that command to finish in order for the 'awk' to start.

Regards.

---

### Post by s1baker on 2012-10-17
Thanks papibe.
I didn't know that. I thought that the '&' meant to wait.

---

### Post by Slim Odds on 2012-10-17
> **s1baker said:**
> Thanks papibe.
I didn't know that. I thought that the '&' meant to wait.
Technically, it means "run in the background" which means "don't wait".

---

