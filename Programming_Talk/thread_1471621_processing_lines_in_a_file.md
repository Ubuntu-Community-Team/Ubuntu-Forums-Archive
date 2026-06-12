---
title: "processing lines in a file"
date: 2010-05-03
forum: Programming Talk
---

### Post by boondocks on 2010-05-03
I am able to add text to the beginning of a line with:
```
sed 's/^/ LINE_start /g' inputfile.txt > outputfile.txt
```
I am able to add text to the end of a line with:
```
sed 's/$/ LINE_stop /g' inputfile.txt > outputfile.txt
```
But how do I add text to the beginning **and** end of a line, **only** if it contains a pattern.
So if the line contains "some food" like:
There is some food in the kitchen.
Then update the line with:
! Eureka ->> There is some food in the kitchen. <<- Found it !

And if the line does not contain "some food" then ignore it.

---

### Post by Portmanteaufu on 2010-05-03
I think backreferences will help you out here, though there may be a more elegant way of doing things.

```

cat myfile.txt | sed 's/^\(.*\)\(some food\)\(.*\)$/!!! Eureka-> \1\2\3 <- Found it!/

```

In the second part of a sed command, \1 refers to "whatever was found in the first set of \(\) parenthases", \2 the second set of parens, etc. This method ensures that "some food" appears someplace in the middle of the line and then reconstructs the line with the necessary additions.

---

### Post by Portmanteaufu on 2010-05-03
As an alternative, if you're just trying to view the contents of a file with the important bits highlighted, you can always do this:

```

grep --color=auto 'pattern|$' file_to_display

```

This will print any line that either:
1.) Contains the pattern you specify
or
2.) Has an end. (That is to say, all of them because every line has an end.)

The result is that all of the lines of the file you specify are dumped to the terminal, but all of the words matching your pattern (e.g. "some food") are in bright red. (The color is configurable via environment variable.)

---

### Post by boondocks on 2010-05-05
> **Portmanteaufu said:**
> I think backreferences will help you out here, though there may be a more elegant way of doing things.

```

cat myfile.txt | sed 's/^\(.*\)\(some food\)\(.*\)$/!!! Eureka-> \1\2\3 <- Found it!/

```

In the second part of a sed command, \1 refers to "whatever was found in the first set of \(\) parenthases", \2 the second set of parens, etc. This method ensures that "some food" appears someplace in the middle of the line and then reconstructs the line with the necessary additions.
Portmanteaufu,
Thank you, once again!

---

