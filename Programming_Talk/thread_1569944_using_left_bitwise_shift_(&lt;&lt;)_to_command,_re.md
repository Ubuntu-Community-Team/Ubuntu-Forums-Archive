---
title: "using left bitwise shift (&lt;&lt;) to command, redirect it to ( &gt; ) output.txt"
date: 2010-09-07
forum: Programming Talk
---

### Post by Claus7 on 2010-09-07
Hello,

I would like to use bitwise left shift to a command so as to be able to give input to this command. This is looking like:

```
command << foo
input
foo
```

so far so good.

Now, I would like this result to direct it as output to an output.txt file somehow like:

```
command > output.txt
```

The problem is how I would be able to to such a task, without messing with the bitwise shifts.

Any idea would be more than welcome.

Regards!

PS: Something like:

> command << foo
input
foo > output.txt

does NOT work.

---

### Post by spjackson on 2010-09-07
```

command > output.txt << foo
input
foo

```

---

### Post by Claus7 on 2010-09-07
Yes Sir!

Exactly what I was looking for.

Thanks a lot!

Regards!

EDIT: I have noticed that if a command follows the above command, then an empty line should be in-between them.

EDIT: Also some times if 'string' cannot have any meaning it seems that the above command should entirely be wiped out and rewritten for some buggy reason!

---

### Post by geirha on 2010-09-07
It's called a here document btw, not a bitwise shift in this context ;)
[http://mywiki.wooledge.org/BashGuide/InputAndOutput#Heredocs_And_Herestrings](http://mywiki.wooledge.org/BashGuide/InputAndOutput#Heredocs_And_Herestrings)

---

