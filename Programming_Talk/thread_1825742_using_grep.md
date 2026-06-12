---
title: "using grep"
date: 2011-08-15
forum: Programming Talk
---

### Post by sum1nil on 2011-08-15
Hi,
I'm trying to use grep on a text file full of method calls all starting with 'G' or 'g_'.
I am very unfamiliar with using reg exps but this almost works:
grep ^[Gg] glib-depreciated.txt 
and gives this type of output.
> 
g_string_up, function in Strings
g_strncasecmp, function in String_Utility_Functions
g_strup, function in String_Utility_Functions
g_tree_traverse, function in Balanced_Binary_Trees
g_tuples_destroy, function in Relations_and_Tuples
g_tuples_index, function in Relations_and_Tuples



However, this gives me the whole line including description. The delimiter, ',', occurs before the description and I would like grep to stop there, however I don't know how.

In short, how do I make grep only list words starting with [Gg] followed by some characters including underscores and then stop when it hits a comma.

Still learning.
TY in advance for any help.

---

### Post by nmaster on 2011-08-15
use cut:
```

grep  ^[Gg] glib-depreciated.txt  | cut -d ',' -f1

```

-d ',' sets the delimiter to a comma
-f1 gets the first field

---

### Post by cgroza on 2011-08-15
I looked into the man page, and could not see any option that could do that.
You could write your own script though.
Here is some Perl:

```


#!/usr/bin/env perl

while(<>)
{
    if(/(^[Gg].*).*,/)
    {
        print "$1\n";
    }
}

```It takes a line, matches it with ^[Gg] and if it matches prints the line before the first comma.

EDIT, nmaster seems to know the Unix tools better than me :D.

---

### Post by nmaster on 2011-08-15
> **cgroza said:**
> I looked into the man page, and could not see any option that could do that.
You could write your own script though.
Here is some Perl:

```


#!/usr/bin/env perl

while(<>)
{
    if(/(^[Gg].*).*,/)
    {
    print "$1\n";
    }
}

```It takes a line, matches it with ^[Gg] and if it matches prints the line before the first comma.

EDIT, nmaster seems to know the Unix tools better than me :D.

this is overkill.  just do what i said.

EDIT: srry, didn't see your edit. didn't mean to look like a jerk. lol

---

### Post by ofnuts on 2011-08-15
> **sum1nil said:**
> Hi,
I'm trying to use grep on a text file full of method calls all starting with 'G' or 'g_'.
I am very unfamiliar with using reg exps but this almost works:
grep ^[Gg] glib-depreciated.txt 
and gives this type of output.



However, this gives me the whole line including description. The delimiter, ',', occurs before the description and I would like grep to stop there, however I don't know how.

In short, how do I make grep only list words starting with [Gg] followed by some characters including underscores and then stop when it hits a comma.

Still learning.
TY in advance for any help.

grep -o will only output the matching string, so if you extend your regexp to only match up to the comma (not included), you should get the right output:
```
grep -o '^[gG][^,]*'  glib-depreciated.txt
```(ie match G or g, followed by any characters that aren't a comma -> stops before first comma)

You can also protect your rear an dbe a bit more restrictive, ie match only what can be a C symbol: alphanumerics plus underscore:
```
egrep -Eo '^[gG][[:alnum:]_]+'  glib-depreciated.txt
```(yes, grep -E or egrep...)

---

### Post by sum1nil on 2011-08-15
Thanks for the tip. Worked perfectly.
Is there a way I can mark your reply as answer or give kudos to those that help on these forums. Just asking.

Thank you.

---

