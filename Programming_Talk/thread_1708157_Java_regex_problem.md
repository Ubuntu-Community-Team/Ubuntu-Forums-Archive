---
title: "Java regex problem"
date: 2011-03-16
forum: Programming Talk
---

### Post by leg on 2011-03-16
I seem to be having a problem matching "\*" as a regex in java.

```

pattern = Pattern.compile("\\*");
matcher = pattern.matcher(contents);

```Matches against "*" characters and 
```

pattern = Pattern.compile("\\\\*");
matcher = pattern.matcher(contents);

```and variations of it such as in a class [] grouping don't work either and still only matches the "*" or occasionally the "\" character. The docs say that you only need to backslash to escape the special characters to have them recognised literally. I have also tried the \\Q\\*\\E string also and that doesn't match either.

Any ideas how I can match "\*" pair of characters. Thanks.

---

### Post by PaulM1985 on 2011-03-16
> **leg said:**
> 
```

pattern = Pattern.compile("\\\\*");
matcher = pattern.matcher(contents);

```

Haven't you got too many \'s here.  Shouldn't you only have 3 '\' and a '*'?  2 '\' for the first '\' and one for the '*'?

Paul

---

### Post by Arndt on 2011-03-16
> **leg said:**
> I seem to be having a problem matching "\*" as a regex in java.

```

pattern = Pattern.compile("\\*");
matcher = pattern.matcher(contents);

```Matches against "*" characters and 
```

pattern = Pattern.compile("\\\\*");
matcher = pattern.matcher(contents);

```and variations of it such as in a class [] grouping don't work either and still only matches the "*" or occasionally the "\" character. The docs say that you only need to backslash to escape the special characters to have them recognised literally. I have also tried the \\Q\\*\\E string also and that doesn't match either.

Any ideas how I can match "\*" pair of characters. Thanks.

I think you need one more pair of backslashes:

```
pattern = Pattern.compile("\\\\\\*");
```

What this Java string really contains is \\\* and the regexp parser will see this as one escaped backslash, followed by one escaped asterisk, so it will match the literal \*.

---

### Post by Vaphell on 2011-03-16
i don't use java but even in python where the concept of raw string exists results are not entirely consistent
```

pattern = [ '[\\\\][*]', r'[\][*]', r'[\\][*]', '.[*]' ]

output:
something\\*\some other junk
[\\][*] => \*
[\][*] => *
[\\][*] => \*
.[*] => \*


```

try some variation of [\\][*] with different number of / or when that fails replace every \ in contents variable with some other unique character and then replace back in results.

---

### Post by Reiger on 2011-03-16
Use litteral patterns: "\\Q\\\\E". The Pattern (java.util.regex.Pattern) class provides ways to construct “difficult” regexes such as these.

---

### Post by leg on 2011-03-16
> **Arndt said:**
> I think you need one more pair of backslashes:

```
pattern = Pattern.compile("\\\\\\*");
```

What this Java string really contains is \\\* and the regexp parser will see this as one escaped backslash, followed by one escaped asterisk, so it will match the literal \*.

Thanks that works.

---

