---
title: "awk print paragraphs greater than 3 lines"
date: 2012-06-06
forum: Programming Talk
---

### Post by thatdamkid on 2012-06-06
I have an HTML File that dumps a bunch of employee info and looks like this.

```

Employee John.Doe
CLO
AGE22
ATN4
OWNER
PERF0
-

Employee Jane.Doe
2yr
-

Employee John.Smith
CLO
AGE22
ATN4
OWNER
PERF0
-

Employee Jane.Smith
weekly
-
...

```

This goes on for 2000 more times

All I want to do is awk out any employee entry that is 3 lines long so that I an left with only the following.

```

Employee John.Doe
CLO
AGE22
ATN4
OWNER
PERF0
-

Employee John.Smith
CLO
AGE22
ATN4
OWNER
PERF0
-


```

Thanks for the time.

---

### Post by steeldriver on 2012-06-06
does it have to be awk? if the records are always delimited by a dash (-) then how about

```
sed '/^Employee/{$!N;$!N;$!N;/-/d}'
```[matches lines starting with 'Employee', then appends the next 3 non-EOF lines (3 not 2 so as to catch the trailing blank line), and deletes the pattern space if it contains a dash]

EDIT: actually that's a bit broken, it will also delete any 4-line records - it would be better to read exactly 'Employee + 2 lines' and then handle any duplicate blank lines resulting from the deletion separately:

```
sed -e '/^Employee/{$!N;$!N;/-/d}' -e '/^$/{$!N; s/\n\n/\n/}'
```

---

### Post by papibe on 2012-06-06
Hi thatdamkid.

This works with your example data.
```
awk 'BEGIN{FS="\n"; RS=""} { if (NF > 3) print $0, "\n";}' ./input.txt

```
Where
[INDENT]'BEGIN' is executed in the beginning of the script to set separators.
'RS=""' means records (the usual lines) are separated by an empty line.
'FS="\n"' set the field separator (spaces by default) to newline.
NF represents how many fields a record have. In this case, how many lines.[/INDENT]
I hope that helps.
Regards.

---

### Post by steeldriver on 2012-06-06
^^^  I love this! I never would have thought to make newline the FS

I learn something new every day

---

