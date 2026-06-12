---
title: "Why does ls -l and find come up with different counts?"
date: 2011-11-23
forum: Programming Talk
---

### Post by saphil on 2011-11-23
There must be some reason why the counts come out so different.  Grep is counting lines with "-c," right?  Does this mean that there are a number of lines with more than one instance of "*.jp2" in them?

```

$ ls -R| grep jp2 -c
96674
$ find -name "*.jp2" | wc -w
1308547

```

---

### Post by San_SS! on 2011-11-23
Two things:
 * Do you happen to have spaces in your paths? Cause in that case wc -w counts the number of words, which is different from the number of lines. To solve that use wc -l instead of wc -w
 * With the grep you're only filtering the ones that have jp2 in the name not that end with that. you should use a regex with grep by giving it the -e argument

Hope this helps!

---

### Post by Bachstelze on 2011-11-23
How about looking at the output of the commands and find out what they do differently?

---

### Post by saphil on 2011-11-23
> **Bachstelze said:**
> How about looking at the output of the commands and find out what they do differently?

Thanks, this makes sense, but...
These are very large directories and even an output of 90000 lines is hard to get through.
Would it make sense to redirect the 2 outputs to a pair of files and run diff on them?

---

### Post by saphil on 2011-11-23
> **San_SS! said:**
> Two things:
 * Do you happen to have spaces in your paths? Cause in that case wc -w counts the number of words, which is different from the number of lines. To solve that use wc -l instead of wc -w
 * With the grep you're only filtering the ones that have jp2 in the name not that end with that. you should use a regex with grep by giving it the -e argument

Hope this helps!

It did help.  I have no idea where the million+ jp2 instances are, but counting lines is far more useful to me, and it also comes to the same answer as ls -l.  (I know that doesn't make it true, but it improves the probability of truth.)

---

### Post by sisco311 on 2011-11-23
Check out BashFAQ #4 (link in my signature) and [http://mywiki.wooledge.org/ParsingLs](http://mywiki.wooledge.org/ParsingLs)

---

### Post by Bachstelze on 2011-11-23
> **saphil said:**
> Thanks, this makes sense, but...
These are very large directories and even an output of 90000 lines is hard to get through.
Would it make sense to redirect the 2 outputs to a pair of files and run diff on them?

Yes, or you can pipe them to [font=monospace]less[/font] for example. the difference should be obvious by just looking at them.

---

### Post by mikejonesey on 2011-11-23
$ ls -R| grep jp2 -c
96674
$ find -name "*.jp2" | wc -w
1308547


to make the ls the same as the find it would have to be;
ls -R | grep -c ".*\.jp2$"

(the extra .* begins with anything, will match the begging can be omited in your case)
(the \. ensures a dot as in find statment)
(the dollar means ends with as in find statment)

to make the find the same as the ls line it would have to be;
find -name "*.jp2*"

(the extra star to say may not end in...)

other differences can be found in the stdout of these commands ie;
mkdir dir dir2
touch dir2/afile
ls -R | grep -c "dir" = 4
find . | grep -c "dir" = 3

finaly as find prints a new line per file you would also want to use the -l instead of -w (a file or directory may have one or more words).

the final command to count;

```
find . -type f "*.jp2" | wc -l
```

---

### Post by sisco311 on 2011-11-24
> **mikejonesey said:**
> 

the final command to count;

```
find . -type f "*.jp2" | wc -l
```

Nope. 

```

[sisco@acme xtmp]$ mkdir foo
[sisco@acme xtmp]$ cd foo
[sisco@acme foo]$ > "file
> name"
[sisco@acme foo]$ ls -1
file?name
[sisco@acme foo]$ find ./ -type f | wc -l
2

```

---

### Post by mikejonesey on 2011-11-24
filename with a line break, lol, will have a look in a mo... :P

---

### Post by saphil on 2011-11-24
The filename with a line-break is interesting.
autocomplete doesn't like it, but if I enter ```
vi file?name
``` it opens for editing and adds lines to the file.

---

