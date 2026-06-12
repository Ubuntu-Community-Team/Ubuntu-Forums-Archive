---
title: "BASH scripting Question -- Indicating the pressing of keys, and the apersand (&amp;)"
date: 2012-08-31
forum: New to Ubuntu
---

### Post by Invectus on 2012-08-31
1. When it comes to bash shell scripting; how do I indicate something such as: "ctrl+(key)" or "alt+(key)", etc..

2.  I know that when you add an apersand (&) behind a command or program as so:

```
#Magical Pixie Dust Start Up

pixiedust.run &
```

It should put it in the background. Sometimes, for me, it doesn't work, and the program still depends upon the CLI used to launch it.

-- The second thing I'd like to know is how does the use of 2 ampersands (&&) work in a bash shell script?

```
#Magical Pixie Dust Start Up & Elf Tears Song Player

pixiedust.run && elftearsongplayer
```

I don't understand the double ampersand in a case like this.

(They're only examples, and the "programs" are fake, by the way!)

---

### Post by Vaphell on 2012-09-01
&& is a boolean logic operator (AND)
consider success=true and failure=false.

evaluation of the expression prog1 && prog2:
1. prog1=false, expression is false (false AND whatever is false so there is no need to execute 2nd step) - any failure in the chain of &&-ed commands breaks the sequence
2. prog1=true, expression depends wholly on the value of the 2nd step so it needs to be run - success allows to run the next step in chain

|| operator (OR) behaves in a similar way.
true OR whatever = true so success means skipping unnecessary step #2
false OR whatever depends on 2nd step so it gets executed - #2 is launched when there is error in the step before.

prog1 && prog2 -> run prog2 if prog1 was successful
prog1 || prog2 -> run prog2 if prog1 failed

```
$ true && echo TRUE || echo FALSE
TRUE
$ false && echo TRUE || echo FALSE
FALSE
```

---

### Post by Bachstelze on 2012-09-01
> **Vaphell said:**
> 
prog1 && prog2 -> run prog2 if **and only if** prog1 was successful
prog1 || prog2 -> run prog2 if **and only if** prog1 failed

To make things a bit more clear. :)

---

### Post by Kopkins on 2012-09-01
For detecting key presses, look up the advanced bash scripting guide. I learned a lot from that guide. Try example 5-3 on pages 45-46. It doesn't have the info for alt, ctrl, etc. but that wouldn't be too hard to find out I bet. Be creative.

The bash guide also has lots of information on your other question.

Best of luck,
Kopkins

---

### Post by Invectus on 2012-09-01
Thanks, but now I have one more question, thus far. How can this be used in branching (if/else/elif)?

---

### Post by Lars Noodén on 2012-09-01
You can get an if-then-else kind of behavior by chaining them all together.

prog1 && prog2 || prog3

If prog1 is successful, then prog2 is run.
If prog1 fails, then prog3 is run.

---

