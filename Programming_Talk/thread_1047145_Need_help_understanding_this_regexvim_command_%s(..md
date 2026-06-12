---
title: "Need help understanding this regex/vim command :%s/\(.*\).c/mv &amp; \1.bla"
date: 2009-01-22
forum: Programming Talk
---

### Post by AncientPC on 2009-01-22
```

    $ vim
    :r! ls *.c
    :%s/\(.*\).c/mv & \1.bla
    :w !sh
    :q!

```

I know what the above lines do, but I need help understanding the :%s command.

For the first half, \(.*\).c is the regex equivalent to *.c for globbing, right?

For the second half, what does the & and \1 represent in the replace pattern?
mv & \1.bla

& means original line?
\1 means the data that matched pattern \(.*\).c?

---

### Post by dribeas on 2009-01-22
> **AncientPC said:**
> 
For the first half, \(.*\).c is the regex equivalent to *.c for globbing, right?

For the second half, what does the & and \1 represent in the replace pattern?
mv & \1.bla

& means original line?
\1 means the data that matched pattern \(.*\).c?

The general form of the substitute expression is:

<where>s[ubstitute]/<pattern_match>/<substitution>/<flags>

<where> is a lines range, where % represents all lines.

<flags> is optional and determines whether more than one match will be done in a single line

Now the pattern and substitution (pattern). A pattern equivalent to *.c glob would be: .*\.c meaning:

```

. any character
* repeated any number of times
\. dot character (note that it is escaped here, probably a mistake in your post).

```

Whenever you add \( and \) to the pattern you are asking the matcher to remember that block in a buffer.  Easier with an example:

```

substitution: s/\(.*\)\.c/\1
input:   filename.c
output: filename

```

The pattern matches any number of any type of characters *.** (remembered in buffer 1: *\(*...*\)* followed by a dot and a c *\.c* with the contents of the buffer *\1*.
A more complex example would be:

```

substitution: s/\(.*\)\.\(.*\)/\2.\1
input:    any_character_sequence.another_sequence
output: another_sequence.any_character_sequence

```

The *&* character represents the whole matched pattern (not the whole line):

```

substitution: s/[0-9]*/-&-
input:   asdfasdfadf2345234adklsfjalsdkf
output:asdfasdfadf-2345234-adklsfjalsdkf

```

You can learn more about it by reading vim help (inside vim use :help substitute)

NOTE: Ignore spaces in all the input/output parts as if they were not present altogether. They are a formatting error in the post

---

### Post by stylishpants on 2009-01-22
> **AncientPC said:**
> ```

    $ vim
    :r! ls *.c
    :%s/\(.*\).c/mv & \1.bla
    :w !sh
    :q!

```

I know what the above lines do, but I need help understanding the :%s command.

For the first half, \(.*\).c is the regex equivalent to *.c for globbing, right?

For the second half, what does the & and \1 represent in the replace pattern?
mv & \1.bla

& means original line?
\1 means the data that matched pattern \(.*\).c?

In case it isn't clear from dribeas' thorough explanation, the \1 includes everything that matched between the \( and \) in the search pattern.  It doesn't include the ".c" part.


Note that the expression as given has the potential problem that it will not properly handle filenames that include the string '.c', but not at the end of the line.
eg.  foo.cpp or foo.c.old-version

This would be easily corrected by appending a $ to the search pattern:
    :%s/\(.*\).c$/mv & \1.bla

Filenames with spaces aren't handled either, but that's less likely to be an issue with source files.

---

### Post by AncientPC on 2009-01-24
Thanks very much to the both you, it makes a lot more sense now. :)

---

