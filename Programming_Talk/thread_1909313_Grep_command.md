---
title: "Grep command"
date: 2012-01-15
forum: Programming Talk
---

### Post by achuth on 2012-01-15
[COLOR=Blue]Sir,
Consider the following file content
[/COLOR]
[COLOR=#000000][FONT=Courier New]This line contains the number 113.          # Match. 
This line contains the number 13.           # No match. 
This line contains the number 133.          # No match. 
This line contains the number 1133.         # Match. 
This line contains the number 113312.       # Match. 
This line contains the number 1112.         # No match. 
This line contains the number 113312312.    # Match. 
This line contains no numbers at all.       # No match.[/FONT]


[FONT=Verdana][COLOR=Blue]Now consider the following command:[/COLOR]
$ grep "1133*" filename

[COLOR=Blue]The output is [/COLOR]
[FONT=Courier New]This line contains the number 113.          # Match.
This line contains the number 1133.         # Match.
This line contains the number 113312.       # Match.
This line contains the number 113312312.    # Match.
[/FONT]
[/FONT][/COLOR]I don't understand why the first line is displayed eventhough there is no "1133".
Why is it so?

---

### Post by adityamagadi on 2012-01-15
it is because you are using * in your grep command

---

### Post by Bachstelze on 2012-01-15
1133* means 113 followed by any number of occurrences of 3, including zero.

man 7 regex

---

### Post by achuth on 2012-01-16
Is this the same for UNIX OS?

---

### Post by Arndt on 2012-01-17
> **achuth said:**
> Is this the same for UNIX OS?

The same as what?

---

### Post by Idyll on 2012-01-17
Yes, it works the same way in UNIX System V and Solaris 2.0.  I just verified in my "UNIX in a Nustshell" book.

The symbol * "matches zero or more preceding" pattern or character specified.

---

