---
title: "awk outputs the input ... that's odd."
date: 2011-05-12
forum: Programming Talk
---

### Post by bruce.staples on 2011-05-12
This may be an *obvious* problem, but I just can't see it!

I have an awk script to extract fields, and output a csv file, but now I'm not able to use it!

I have an input of the following format:

[INDENT][FONT="Courier New"]START:1
FIELD_1:content11
FIELD_2:content12
FIELD_3:content13
END
START:2
FIELD_1:content21
#FIELD_2:content22
FIELD_3:content23
END
START:3
FIELD_1:content31
FIELD_2:content32
FIELD_3:content33
END[/FONT][/INDENT]

The awk script is:

[INDENT][FONT="Courier New"]!/bin/awk
BEGIN {
        FS =":"
        print "Fieldname1,Fieldname2,fieldname3"
        }
/^FIELD_1/ {
        field1 = $2
        }
/^FIELD_2/ {
        field2 = $2
        }
/^FIELD_3/ {
        field3 = $2
        }
/^END/ {
        print field1  "," field2 "," field3
        # messy clean up for each record
        field1 = ""
        field2 = ""
        field3 = ""
        }
#[eof]
[/FONT][/INDENT]

So invoking it with
[INDENT][FONT="Courier New"]$ awk -f e.awk input.txt > output.txt[/FONT][/INDENT]

I expected


[INDENT][FONT="Courier New"]Fieldname1,Fieldname2,fieldname3
content11,content12,content13
content21,,content23
content31,content32,content33[/FONT][/INDENT]

but I got:

[INDENT][FONT="Courier New"]Fieldname1,Fieldname2,fieldname3
START:1
FIELD_1:content11
FIELD_2:content12
FIELD_3:content13
END
content11,content12,content13
START:2
FIELD_1:content21
#FIELD_2:content22
FIELD_3:content23
END
content21,,content23
START:3
FIELD_1:content31
FIELD_2:content32
FIELD_3:content33
END
content31,content32,content33
[/FONT][/INDENT]

... which is apparently echoing the input to the output ...
This happens with 
[INDENT][FONT="Courier New"]awk -f e.awk input.txt[/FONT][/INDENT]
as well.
Any suggestions (please)?

---

### Post by erind on 2011-05-12
Remove this line from the beginning of the awk script:

```
[COLOR=Red]!/bin/awk[/COLOR]
```You're already using awk *outside*, to call the script: **awk** -f e.awk.

---

### Post by cgroza on 2011-05-13
> **erind said:**
> Remove this line from the beginning of the awk script:

```
[COLOR=Red]!/bin/awk[/COLOR]
```You're already using awk *outside*, to call the script: **awk** -f e.awk.
I think that line should have a "#" in front. So it would become:
```
[COLOR=Red]#!/bin/awk[/COLOR]
```

---

### Post by matt_symes on 2011-05-13
Hi

There are many things wrong with the script the least of which is

```
matthew@matthew-laptop:~$ which awk
/usr/bin/awk
matthew@matthew-laptop:~$ 
```

Is this homework ?

Kind regards

---

### Post by bruce.staples on 2011-05-15
*BINGO!*
Yes the missing hash in the first line was it!
Thanks cgroza.
And Matt, yes, I seem to have mislaid awk, but as I had invoked it from the command line, the bad location was ignored (once the hash was inserted).

Thanks all ...

---

### Post by erind on 2011-05-15
Glad you got it working. Just to clarify it again: The way you're calling the script *"awk -f e.awk input.txt*" , the line "*!/bin/awk"* is wrong where it is, because awk will interpret it as a _valid pattern to be evaluated_, and not as awk interpreter, which you probably thought it would do. As I mentioned before, it's awk outside of the script that takes care of it:   *[COLOR=Magenta]awk[/COLOR]* *-f e.awk ...*
With the hash before it - *"#!/bin/awk*", it'd be interpreted as only a _simple comment_, nothing else - as you noticed it was ignored.
If you still want to have the script the way you wrote it before ( with *!/bin/awk *), then precede that line with **#** as suggested and add **-f **at that line's end, make the file* e.awk* executable and run it as a stand-alone script, like so:

```
$./e.awk input.txt > output.txt

$ type awk
awk is /usr/bin/awk

$ cat e.awk
[COLOR=Magenta]#!/usr/bin/awk -f[/COLOR]

BEGIN {
  FS =":"
  ...
# more code here ... 
}
```You can read more on how to run awk at: [http://www.gnu.org/software/gawk/manual/gawk.html#Long](http://www.gnu.org/software/gawk/manual/gawk.html#Long)

Hope it helps.

---

### Post by matt_symes on 2011-05-15
Hi

> You can read more on how to run awk at: [http://www.gnu.org/software/gawk/manual/gawk.html#Long](http://www.gnu.org/software/gawk/manual/gawk.html#Long)And if you are wondering why it's gawk. It's because it's linked to though your alternatives (assuming you have not changed where it points to).

```
matthew@matthew-laptop:~$ which awk
/usr/bin/awk
matthew@matthew-laptop:~$ ls -l /usr/bin/awk
lrwxrwxrwx 1 root root 21 2011-05-08 22:35 /usr/bin/awk -> /etc/alternatives/awk
matthew@matthew-laptop:~$ ls -l /etc/alternatives/awk
lrwxrwxrwx 1 root root 13 2011-05-08 22:35 /etc/alternatives/awk -> /usr/bin/gawk
matthew@matthew-laptop:~$ readlink -f /usr/bin/awk
/usr/bin/gawk
matthew@matthew-laptop:~$ 
```The symbolic link /usr/bin/awk points to  /usr/bin/gawk via the alternatives symbolic link in /etc/alternatives/awk.

Gawk is the default implementation of awk in Ubuntu.

Kind regards

---

