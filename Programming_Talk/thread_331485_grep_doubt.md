---
title: "grep doubt"
date: 2007-01-04
forum: Programming Talk
---

### Post by jordilin on 2007-01-04
I have the following files:
hla.txt
hhla.txt
hhhhla.txt
Why when I type:
```
ls | grep h*
```
I get nothing. I thought that the regular expression * means zero or more matches of the preceding character, so I should get the three files. If I do ```
ls | grep h*la
``` then, obviously I get the three files listed. Any good explanation??

---

### Post by meng on 2007-01-04
Why use grep at all? Just
ls h*
Here, * substitutes for any number of characters, and not just 'h' characters.

---

### Post by jordilin on 2007-01-04
> **meng said:**
> Why use grep at all? Just
ls h*
Here, * substitutes for any number of characters, and not just 'h' characters.

Yes, you are right, but I'm learning regular expressions, and I would like to know why grep h* doesn't come up with any result.

---

### Post by hod139 on 2007-01-04
With grep you have to escape the metacharacters (? not 100% sure what they are called) with a "\".  So your command would become
```

ls | grep h\*la
```

---

### Post by lloyd_b on 2007-01-04
First off - "*" is a *shell* wildcard, NOT a regex wildcard.  In regular expressions, the "*" operator is used to specify "zero or more repetitions of the preceding character".

If you want all lines that start with the letter "h", then the correct syntax is "grep ^h".  The "^" specifies "start of line", so the regex translates to "all lines the consist of the sequence <start of line><letter h>"

May I suggest reading the man page for grep?  It contains tons of useful information on regex's that can be used with grep.

Lloyd B.

---

### Post by duff on 2007-01-04
like lloyd said, the * character is being expanded by the shell.  you can prevent this by using single tick marks:
```
# echo h*
hhhhla.txt hhla.txt hla.txt
# echo 'h*'
h*
```
so if you type the command```
# ls | grep 'h*'
``` you should get what you're looking for.

BTW, if you're going to try a compicated regex, you may need to pass the -e parameter.  check the man page.

---

### Post by amo-ej1 on 2007-01-05
When you use strace you can see how the program gets executed. e.g.

```

e@lap:~$ ls | strace grep e* 2>&1 | grep execve
execve("/bin/grep", ["grep", "ea", "eagle", "echo2.pdf", "echo3.pdf", "echo.pdf"], [/* 30 vars */]) = 0

```

'execve' is the systemcall to launch a new binary, the second argument contains the parameters passed. And in this example you clearly see how the e* got expanded to an array.

---

