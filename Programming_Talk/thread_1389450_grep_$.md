---
title: "grep $"
date: 2010-01-24
forum: Programming Talk
---

### Post by piyush.neo on 2010-01-24
why **grep $ **matches each line of a file...
and if it do so then why **grep \$ **also do it...
:confused:

---

### Post by sisco311 on 2010-01-24
The caret ^ and the dollar sign $ are meta-characters that respectively match the empty string at the beginning and end of a line.

'\$' matches the dollar $ sign.

---

### Post by piyush.neo on 2010-01-24
yeah i know...so why are they are showing a positive match for every line in the file???

---

### Post by falconindy on 2010-01-24
Because every line ends with a newline character.

grep '\$' file

The above will match $ characters in a file.

---

### Post by piyush.neo on 2010-01-24
ooopps..i forget to put quotes in second case(grep \$)..
now its matching the $ character...Thanks...
But why was it matching with every line when it was not quoted...
why...???:(:(
(Actully it is exercise of The Unix Programming Enviroment -Keringhan and Pike  page 79 exercise 3.3 and given there without quotes...)

---

### Post by falconindy on 2010-01-24
> **piyush.neo said:**
> But why was it matching with every line when it was not quoted...
why...???:(:(

> **falconindy said:**
> Because every line ends with a newline character.

this thread is starting to seem like a broken record... You're seeing different behavior because your book isn't using the GNU version of these utilities.

---

### Post by Vox754 on 2010-01-30
> **falconindy said:**
> this thread is starting to seem like a broken record... You're seeing different behavior because your book isn't using the GNU version of these utilities.

I think the current behavior is due to shell expansion, that is, the shell makes a first pass and expands some symbols, then it passes the result to grep.

In
```

grep \$    or    grep $    or    grep '$'    or    grep "$"    or    grep "\$"

```
the argument is a single dollar sign
```

ARG = $

```

Double quotes permit shell expansion.
By using single quotes, the shell expansion is avoided. 

In
```

grep '\$'

```
the argument is the string
```

ARG = \$

```
Internally grep understands the string as a regular expression and does its stuff.

Another way to pass the string is to escape the escape character
```

grep \\$

ARG = \$

```

Escape the escape character and then the dollar symbol
```

grep \\\$

ARG = \$

```

This is the reason many commands like "sed", or "find" use single quotes in the arguments, not because it's a requirement, but to avoid shell expansion. It should be possible to escape the symbols and have the same result, but it becomes messy with so many backslashes \.

For example
```

sed 's/[[:digit:]]//g'

sed s\/\[\[\:digit\:\]\]\/\/g

```

---

