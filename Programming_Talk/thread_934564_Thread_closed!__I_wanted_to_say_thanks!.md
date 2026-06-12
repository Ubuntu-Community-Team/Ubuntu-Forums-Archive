---
title: "Thread closed!  I wanted to say thanks!"
date: 2008-09-30
forum: Programming Talk
---

### Post by nuclearj on 2008-09-30
to Jacobmp92, you are correct.  I will learn more by studying.  I got that O'Reily book and it's great!

And I solved that problem from before:
[http://ubuntuforums.org/showthread.php?t=925257](http://ubuntuforums.org/showthread.php?t=925257)

```

a = raw_input("enter string to decode:\n")

for solu in a:
	s = ord(solu)+2
	#print ord(solu)+2,
	if s == 123:
		s = 97
	if s == 124:
		s = 98
	if s == 41:
		s = 44
	if s == 34:
		s = 32	
	for solu2 in solu:
		print chr(s),

```

Thought: Does this code look like a child learning how to draw/write to you experienced programmers?

Thanks again Jacob!

---

### Post by drubin on 2008-09-30
GLad you learnt something!!

Hopefully this others will read  it and learn something from it and do homework problems out on their own.

---

### Post by dwhitney67 on 2008-09-30
actually it would be better if there were if-elses, not just ifs in the code.

---

