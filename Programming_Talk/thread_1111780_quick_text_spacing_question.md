---
title: "quick text spacing question"
date: 2009-03-31
forum: Programming Talk
---

### Post by lems on 2009-03-31
I have an output like this...

```

10000 	0	0	0	0
50000 	10	20	10	10
100000 	20	40	40	20
500000 	120	220	210	190
1000000 	260	450	450	480
5000000 	1250	2300	2970	3470
10000000 	2470	4780	6770	7980
```

The spacing is off because the values run into the tab character. How do I fix this? Is there away to specify how big the tab character is?

This is from the shell by the way. I'm using shell commands to compute and spit out values.

---

### Post by ghostdog74 on 2009-03-31
you can use printf and its justification (- sign) format specifiers. check the man page of printf for more info

---

### Post by lems on 2009-03-31
hmm this isn't working for me... maybe I'm doing it wrong, but the c commands don't act the same way in shell?...

---

### Post by ghostdog74 on 2009-03-31
printf exists as a shell command. check the man page.

---

### Post by lems on 2009-03-31
> **ghostdog74 said:**
> printf exists as a shell command. check the man page.

ahh i got it.. was using it incorrectly...

---

