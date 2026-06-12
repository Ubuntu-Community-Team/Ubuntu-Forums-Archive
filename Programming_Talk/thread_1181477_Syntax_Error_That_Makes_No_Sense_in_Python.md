---
title: "Syntax Error That Makes No Sense in Python"
date: 2009-06-07
forum: Programming Talk
---

### Post by StunnerAlpha on 2009-06-07
Ey guys, here is the relevant portion of code:

```

def _parseAction(fline):
	if fline[G.nextIndex+1] == "\n":
		return fline[G.nextIndex]
	else:
		G.nextIndex += 1
		return ' '.join((fline[G.nextIndex],_parseAction(fline))
	
def _parse(file): #problematic line
	f = open(file)
	line = f.readline()
	fline = line.split()
	fline.append('\n')

```
and this is the error I am getting:
```

File "/Users/.../FLPModule.py", line 50
    def _parse(file):
      ^
SyntaxError: invalid syntax

```
Any idea what is up? Thanks.

---

### Post by soltanis on 2009-06-07
Can we see the lines before that? Sometimes python chokes because there was an error somewhere before. Or maybe it just doesn't like your single underscore. Or maybe it just decided it didn't want you to define a function there.

---

### Post by lisati on 2009-06-07
I'm no Python guru but I suspect the line above the one triggering the error:
> return ' '.join((fline[G.nextIndex],_parseAction(fline))

Unless I'm mistaken there's a mismatch between the number of "(" and the number of ")"

---

### Post by StunnerAlpha on 2009-06-08
> **lisati said:**
> I'm no Python guru but I suspect the line above the one triggering the error:

Unless I'm mistaken there's a mismatach between the number of "(" and the number of ")"
Correctomundo my friend... can't believe I didn't think of that. Thanks a lot guys.

---

### Post by lisati on 2009-06-08
> **StunnerAlpha said:**
> Correctomundo my friend... can't believe I didn't think of that. Thanks a lot guys.

And I just noticed a typo of my own......

---

