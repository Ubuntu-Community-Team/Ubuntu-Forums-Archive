---
title: "Script to change the n-th character of a line in a text file"
date: 2006-09-13
forum: Programming Talk
---

### Post by MacMan on 2006-09-13
Ciao,
As an exercise, I'm trying to write a very simple script that takes a text file, and for certain lines of it, changes the n-th character to a constant.

For example, I'd like to change the 10th character of the comment lines of the /etc/X11/xorg.conf file to an X.

I thought sed would be the best choice for such a job. So that's what I wrote in a shell:
```
$ head /etc/X11/xorg.conf | sed /\(^#.{8}\)\(.\)\(.*$\)/s/\2/X/ -

```

That's how I've conceived it. Obviously I use the s/// command: I created a matching regular expression with three groups:
\1 Should be the beginning of a comment line (^#) followed by ten characters;
\2 should be the 10th character
\3 is the rest of the line
So sed should match any line beginning with a # and change the 10th character with an X.

It doesn't work. :-) It just spits my text file perfectly unchanged.

Any idea of what I'm doing wrong and which is the right way to do this?

Thank you in advance for any help.

Ciao.
-- 
Mac

---

### Post by LotsOfPhil on 2006-09-13
You have almost everything right.
1) You need to escape the curly braces { and } with a backslash \
2) You (maybe, depending on your shell) need to put the expression in single quotes ' '
3) I don't know if your syntax is correct, but I changed it a little to just make it one s expression.

head /etc/X11/xorg.conf | sed 's/\(^#.\{8\}\)\(.\)\(.*$\)/\1X\3/'

I hope this helps.

---

### Post by LotsOfPhil on 2006-09-13
Oh yeah, the reason it just spit it back unchanged is because it wasn't matching anything. sed prints out all lines. If you do sed -n it will only print lines that are matched/changed. Take your original expression and put in -n, it will print nothing.

---

### Post by MacMan on 2006-09-13
> **LotsOfPhil said:**
> 
3) I don't know if your syntax is correct, but I changed it a little to just make it one s expression.

head /etc/X11/xorg.conf | sed 's/\(^#.\{8\}\)\(.\)\(.*$\)/\1X\3/'


Thank you a lot for your help.

No my syntax wasn't correct. Without escaping the curly braces, my regexp wasn't matching any lines. Escaping them, and putting single quotes around the sed command, I was getting a syntax error:
Invalid back reference

I haven't read through the sed's manual, but I guess I can back-reference only the regexp in the s command, not outside of it. So your way is the only way to obtain what I was trying to do.

Anyway: you helped me a lot. Now I understand the whole thing a little bit better. :-) Thank you again.

Ciao.
-- 
Mac

---

### Post by ghostdog74 on 2006-09-13
An example Python alternative:
```

line = open("/etc/X11/xorg.conf").readline()
line = list(line)
line[9] = 'X'
print ''.join(line)

```

---

### Post by MacMan on 2006-09-14
> **ghostdog74 said:**
> An example Python alternative

Thank you very much. Cool use of *list* :-) (I'm still a beginner in Python... too).

But isn't it simpler doing something like:
```
print line[:10] + 'X' + line [12:]
```

Just wondering...

Thank you again.
Ciao.
-- 
Mac

---

### Post by thumper on 2006-09-14
> **ghostdog74 said:**
> An example Python alternative:
```

line = open("/etc/X11/xorg.conf").readline()
line = list(line)
line[9] = 'X'
print ''.join(line)

```

Which doesn't unfortunately check the length of the line, nor if it is a comment.

---

### Post by ghostdog74 on 2006-09-14
> **thumper said:**
> Which doesn't unfortunately check the length of the line, nor if it is a comment.

```

lengthline = 20
for line in open("/etc/X11/xorg.conf"):
    if len(line) < lengthline and line.startswith("#"):
        line = list(line)
        line[10] = 'X'
        print ''.join(line)

```

> 
Thank you very much. Cool use of list  (I'm still a beginner in Python... too).

But isn't it simpler doing something like:
Code:

print line[:10] + 'X' + line [12:]


Just wondering...

Thank you again.
Ciao.


Yup, sure can. Just another way of doing things..

---

### Post by thumper on 2006-09-15
Computationally speaking, it would be more efficient to use string slices rather than a list conversion.

Also the index should be 11 not 12 for the start of the second string.

```
def change_nth(input, nth, replace):
  if nth < 1: raise RuntimeError('replacement position starts at 1')
  if len(input) < nth or not input.strip().startswith('#'):
    return input
  return input[:nth-1] + replace + input[nth:]
```

---

### Post by ghostdog74 on 2006-09-15
I think it depends. what if user wants to change the characters at a few places? 
then the method of slices would be cumbersome to write. Just my opinion.

---

