---
title: "Some grep Help"
date: 2006-06-18
forum: Programming Talk
---

### Post by souled on 2006-06-18
Alright, I need a little bit of help. How can I use grep to show only certain words in a line rather than the whole line? Or can it not be done with grep?

Here is what I'm trying to do.
If I use this command: ```
 hellanzb.py status | grep % 
```
I get this output: ```
 492.0KB/s, 2736 MB queued, ETA: 01:34:56 (42%) 
```

I want to be able to just extract the % done (without the % sign). In this case, I would want 42 (the answer to life?) to be displayed. What is the best way to do this?

Thanks for the help.

---

### Post by fritz_monroe on 2006-06-18
I'm definately not an expert, but how about using the -o switch?  It's supposed to display only the portion of the line that matches the pattern you supply.

---

### Post by souled on 2006-06-18
Yeah, I just saw that switch, but it doesn't display everything. If I grep for %, then it will only reply with '%.' The number in front is what I need.

Also, Is there a way to knock off leading white space in a line through grep?

---

### Post by Third Thoughts on 2006-06-18
If you just want to display the number and the percent sign how about 
```
grep -o [[:alnum:]]*%
```
I gave it a few test runs and it dealt with whitespace as well as random numbers not next to percent signs.

---

### Post by souled on 2006-06-19
Thanks. Exactly what I need.

---

### Post by Arndt on 2006-06-20
[QUOTE=souled]
Also, Is there a way to knock off leading white space in a line through grep?[/QUOTE]

Can you be more specific? There probably is a way to do what you want, with 'sed' and 'perl' if not with 'grep', but I don't see exactly what you want.

---

### Post by Third Thoughts on 2006-06-20
[QUOTE=Arndt]Can you be more specific? There probably is a way to do what you want, with 'sed' and 'perl' if not with 'grep', but I don't see exactly what you want.[/QUOTE]

I think I know how you could knock off leading whitespace with grep. If you're only dealing with letters and numbers then you can type
```
 grep -o [[:alnum:]].* 
```
If you throw punctuation in its slightly more complicated, but not bad.
```
 grep -o [[:alnum:][:punct:]].* 
```
Its the same basic principle. Just set grep so it only displays the matching string and make it so that you match any string that doesn't start with a space.

~Andrew S.

---

### Post by zentagonist on 2007-11-11
Is there any way to do something similar without using the -o switch? And if not, is there anything other than grep that can do it?

If I have a file that contains, for example:

> dog54 is still loose
dog76 is agressive
dog167 has been captured

and all I want is the list of dogs, ignoring everything else in the file ... so the output would be:

> 
dog54
dog76
dog167

is there any way to do this, grepping or otherwise?

---

### Post by ghostdog74 on 2007-11-11
> **zentagonist said:**
> is there any way to do this, grepping or otherwise?

Have you heard of awk? 
```

awk '{
    for( i=1;i<=NF;i++ )
    {
        if($i ~ /dog/) {
            print $i;
        }
    }
     }' "file"

```
output:
```

 # ./test.sh
dog54
dog76
dog167

```

---

### Post by geirha on 2007-11-11
for the doglist I would use cut.
```
cut -d" " -f1 the_file.txt
```
with your example:
```
$ cat << EOF | cut -d" " -f1
> dog54 is still loose
> dog76 is agressive
> dog167 has been captured
> EOF
dog54
dog76
dog167

```

---

### Post by ghostdog74 on 2007-11-11
> **geirha said:**
> for the doglist I would use cut.
```
cut -d" " -f1 the_file.txt
```
with your example:
```
$ cat << EOF | cut -d" " -f1
> dog54 is still loose
> dog76 is agressive
> dog167 has been captured
> EOF
dog54
dog76
dog167

```

yes, it does work, but only if all the dogs are in the same columns. It won't work if the dogs are elsewhere.

---

### Post by geirha on 2007-11-11
Some more information on how the lines may differ would help, though from this information, it sounds like grep is the best way to go:
```
egrep -o "dog[[:digit:]]+"
```

---

### Post by ghostdog74 on 2007-11-11
> **geirha said:**
> Some more information on how the lines may differ would help, though from this information, it sounds like grep is the best way to go:
```
egrep -o "dog[[:digit:]]+"
```

how about this

egrep -o "(dog|dog[[:digit:]]+)" file

in case there is no numbers behind dog

---

### Post by geirha on 2007-11-11
[[:digit:]]+ means 1 or more digits
[[:digit:]]* means 0 or more digits
so in that case this is better ```
egrep -o "dog[[:digit:]]*"
```

---

