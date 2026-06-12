---
title: "[python]logging output and displaying"
date: 2008-08-15
forum: Programming Talk
---

### Post by Pyro.699 on 2008-08-15
Hello,

Im almost 100% sure that this can be done but how would you go about logging all the output (similar to going python file.py > file.txt) but also allowing the output to be displayed in the terminal.

Thanks
~Cody Woolaver

---

### Post by days_of_ruin on 2008-08-15
```
outfile = open("log.txt,'w')
print >> outfile, "anystring"
print "anystring"
```

---

### Post by Pyro.699 on 2008-08-15
what about when using "sys.stdout.write"

---

### Post by days_of_ruin on 2008-08-15
> **Pyro.699 said:**
> what about when using "sys.stdout.write"
Don't bother to use that.Thats why there is ">>".You will have to 
find every print statement and just use two like I posted above.

---

### Post by deuce868 on 2008-08-15
I don't know about that, I mean why find/replace through your code when you can just redirect stdout and avoid all that?

[http://www.faqs.org/docs/diveintopython/kgp_stdio.html](http://www.faqs.org/docs/diveintopython/kgp_stdio.html)

Definite thing you're better off remapping stdout at the top of the script and leave your prints alone.

---

