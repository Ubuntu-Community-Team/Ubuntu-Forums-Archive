---
title: "Sed select between two patterns"
date: 2010-10-19
forum: Programming Talk
---

### Post by ThexDarksider on 2010-10-19
Hello, I've been trying to do this for quite a while now, and I still haven't figured it out (sed is incredibly complicated and I've never used it before a lot). What I'm trying to do is select everything between two patterns, **excluding** the aforementioned patterns. Now the two problematic things about it: it's all on the same line, and there are more... "chunks" to select. For example:  AAAABBBBCCCCAAAADDDDCCCC  I want it to output BBBBDDDD. Is this actually even possible? Although I'd *really* like if you gave me an example with sed, I guess awk would work too, if there's no other way. Oh well.

---

### Post by Some Penguin on 2010-10-19
Looks pretty simple for Perl, anyway.

```

# .*? = Perl-ese for non-greedy match
# /g for global (all matches)
# () for capturing group
my $sz = "AAAABBBBCCCCAAAADDDDCCCC";
while ($sz =~ /AAAA(.*?)CCCC/g) {
   print $1, "\n";
}

```

That's Perl, but sed and awk likely have very similar capabilities.

---

### Post by ThexDarksider on 2010-10-19
Hmm, I don't know Perl, but I'll try to adapt it for sed. Doesn't look too difficult. [s]I'll try it after I sleep for a while, been up for a long time...[/s]

Oh well, I figured it out all by myself, I had to pipe sed through sed. Break one line into more lines.

```
echo AAAABBBBCCCCAAAADDDDCCCC | sed "s/CCCC/\n/g" | sed 's/.*AAAA//g;$d'
```That is exactly what I needed. I hope this will help someone else too. Now I'm thinking with regexps! lol

---

### Post by ghostdog74 on 2010-10-19
Forget about sed, use awk. They both have the same capabilities, BUT awk is more powerful since its also a programming language. 
```


$  echo "AAAABBBBCCCCAAAADDDDCCCC" | awk 'BEGIN{RS="CCCC";FS="AAAA"}RT{print $2 }' 
BBBB
DDDD


```

This says, Set the record separator as "CCCC", then set field separator as "AAAA". now, the 2nd field will be what you want.

---

### Post by DaithiF on 2010-10-20
another sed solution:
```
echo AAAABBBBCCCCAAAADDDDCCCC | sed -r 's/AAAA([^C]*)CCCC/\1/g'
BBBBDDDD
```

---

### Post by ghostdog74 on 2010-10-20
> **DaithiF said:**
> another sed solution:
```
echo AAAABBBBCCCCAAAADDDDCCCC | sed -r 's/AAAA([^C]*)CCCC/\1/g'
BBBBDDDD
```

what if the pattern is ```
 AAAABBCBBCCCCAAAADDDDCCCC  
``` ?
the output should be ```
BBCBB
```

```

#  echo "AAAABBCBBCCCCAAAADDDDCCCC" | awk 'BEGIN{RS="CCCC";FS="AAAA"}RT{print $2 }'
BBCBB
DDDD

# echo AAAABBCBBCCCCAAAADDDDCCCC | sed -r 's/AAAA([^C]*)CCCC/\1/g'
AAAABBCBBCCCCDDDD  <------wrong


```

---

### Post by DaithiF on 2010-10-20
> **ghostdog74 said:**
> what if the pattern is ```
 AAAABBCBBCCCCAAAADDDDCCCC  
``` ?


if that had been the requirement then i might have offered a different solution.
e.g.
```
echo "AAAABBCBBCCCCAAAADDDDCCCC" | sed -e :a -e '/AAAA.*CCCC/{s/CCCC//;s/AAAA//;ta}'
BBCBBDDDD

```

I agree with you though that awk is a better fit for this problem.  But when you say forget sed, just use awk, since it can do what sed can do, and more, thats where I disagree with you (assuming you mean that generally and not just in the context of this specific problem).  Its the same discussion we had back here: [http://ubuntuforums.org/showthread.php?p=8568137](http://ubuntuforums.org/showthread.php?p=8568137), and I guess neither of us have changed our minds since :) .  I still love sed, I still use sed and awk, and I would still recommend people to learn both.

---

### Post by ghostdog74 on 2010-10-20
> **DaithiF said:**
> 
 (assuming you mean that generally and not just in the context of this 
specific problem).  Its the same discussion we had back here: 

yes, i do mean it in general. And yes, i still stand by my point of view. There is no need to learn sed at all. awk does what sed does, and a lot more. See [http://awk.info](http://awk.info) for some projects done with awk.

---

### Post by ghostdog74 on 2010-10-20
> **DaithiF said:**
> if that had been the requirement then i might have offered a different solution.
e.g.
```
echo "AAAABBCBBCCCCAAAADDDDCCCC" | sed -e :a -e '/AAAA.*CCCC/{s/CCCC//;s/AAAA//;ta}'
BBCBBDDDD

```

and what if the pattern is like
```

# echo "AAAABBCBBCCCCAAAADDDD" | sed -e :a -e '/AAAA.*CCCC/{s/CCCC//;s/AAAA//;ta}'
BBCBBAAAADDDD <<----wrong


# echo "AAAABBBBCCCCAAAADDDD" | awk 'BEGIN{RS="CCCC";FS="AAAA"}RT{print $2 }'
BBBB


```
the output should be ```
BBBB
```

---

