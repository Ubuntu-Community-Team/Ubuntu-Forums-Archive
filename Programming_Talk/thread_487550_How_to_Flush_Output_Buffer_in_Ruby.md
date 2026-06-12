---
title: "How to Flush Output Buffer in Ruby?"
date: 2007-06-29
forum: Programming Talk
---

### Post by Ubuntist on 2007-06-29
I'm debugging a Monte Carlo simulation written in Ruby.  At the beginning of each Monte Carlo trial, my code does a ```
puts trialNum
``` where trialNum is the iteration counter.  Unfortunately, this output often fails to appear in until the program has finished running.  I guess the output is being buffered.  Is there a way to flush the buffer, so that these little progress reports appear in real time?

---

### Post by geraldm on 2007-06-29
puts trialNum
$stdout.flush # (depends on OS, but should work)

---

### Post by Ubuntist on 2007-07-01
Yo, dude, thanks!  It works a treat.

---

### Post by santi740 on 2010-10-07
didnt work for me, i get this error

cliente.rb:16: undefined local variable or method `stdout' for main:Object (NameError)

---

### Post by stylishpants on 2010-10-07
> **santi740 said:**
> didnt work for me, i get this error

cliente.rb:16: undefined local variable or method `stdout' for main:Object (NameError)

It's $stdout, not stdout.

---

