---
title: "AWK regexp problem"
date: 2010-01-23
forum: Programming Talk
---

### Post by sinbadbuddha on 2010-01-23
I used a regular expression, /[a-zA-Z0-9_-]{8,12}/ to match any Youtube video ID, but it matches nothing, and will only match of one character is repeated 8-12 times. I'm using GNU awk. Any solutions?

---

### Post by ibuclaw on 2010-01-23
The expression:
```
\w
```
Should should match any of the below without issue.
```
[A-Z][a-z][0-9]_-
```
Regards
Iain

---

### Post by ibuclaw on 2010-01-23
Also, the default installed in Ubuntu is **mawk**, which apparently doesn't support {} matches.

You can, however achieve this by installing gawk.
```
sudo apt-get install gawk
```
and use:
```
awk --posix
```
or
```
gawk --posix
```

If this proves to be tedious, you can always set an alias.

Regards
Iain

---

### Post by Trumpen on 2010-01-23
With gawk, you have to enable them with the option --re-interval:

[QUOTE="man gawk"]       --re-interval
              Enable  the  use of interval expressions in regular expression matching (see Regular Expressions, below).  Interval expressions were not traditionally available in the AWK language.  The
              POSIX standard added them, to make awk and egrep consistent with each other.  However, their use is likely to break old AWK programs, so gawk only provides them  if  they  are  requested
              with this option, or when --posix is specified.[/QUOTE]

You can use [:alnum:] in the place of [a-zA-Z0-9]:

[PHP]gawk --re-interval '/[[:alnum:]_-]{8,12}/'[/PHP]

---

### Post by sinbadbuddha on 2010-01-23
Thanks. Works perfectly now ;)

---

### Post by sinbadbuddha on 2010-01-23
Sorry, not quite. --re-interval works on the command line, but when I add it to the slashbang like so:
```
#!/usr/bin/gawk --re-interval -f
```
gawk just outputs the help. I understand not :confused:

---

### Post by raffaele181188 on 2010-01-23
??? What are you trying to do? :D
```

#!/bin/sh
gawk .....

```
;)

---

### Post by sinbadbuddha on 2010-01-23
> **raffaele181188 said:**
> ??? What are you trying to do? :D
```

#!/bin/sh
gawk .....

```
I'm adding ```
#!/usr/bin/gawk [options] -f
``` to the beginning of an AWK script, to make execution simpler.
```
#!/bin/sh gawk [options] -f
``` generates an error message. As for using a one-line shell script, that's just ugly.

---

### Post by raffaele181188 on 2010-01-24
Oh, ok.
Then I think you should remove the '-f' since
> 
-f _program-file_
--file _program-file_
  Read  the  AWK  program source from the file program-file, instead of from the first command line argument.  Multiple -f (or --file) options may be used.



---

### Post by sinbadbuddha on 2010-01-24
No, that (unfortunately) doesn't help. 
```

#!/usr/bin/gawk -f
# rest of awkscript..

```has always worked on my system; if you leave off the '-f' gawk tries to execute your filename. My problem is that this seems to fail when I add the '--re-interval' option.
```

#!/usr/bin/gawk -f awkscript.awk
#rest of awkscript

```executes the command 
/usr/bin/gawk -f awkscript.awk awkscript.awk
which again tries to parse your filename.

---

### Post by ibuclaw on 2010-01-24
> **sinbadbuddha said:**
> No, that (unfortunately) doesn't help. 
```

#!/usr/bin/gawk -f
# rest of awkscript..

```has always worked on my system; if you leave off the '-f' gawk tries to execute your filename. My problem is that this seems to fail when I add the '--re-interval' option.
```

#!/usr/bin/gawk -f awkscript.awk
#rest of awkscript

```executes the command 
/usr/bin/gawk -f awkscript.awk awkscript.awk
which again tries to parse your filename.

[http://hibernia.jakma.org/~paul/awk-faq.html#script-args](http://hibernia.jakma.org/~paul/awk-faq.html#script-args)

The short answer is that you can't do that.

Regards
Iain

---

### Post by sinbadbuddha on 2010-01-24
Thanks! :(

---

### Post by raffaele181188 on 2010-01-24
:(

---

