---
title: "sed expression question"
date: 2010-09-01
forum: Programming Talk
---

### Post by PryGuy on 2010-09-01
Good day everyone!
Sorry to ask but how do I say in sed "if 'string1' does not exist add 'string2' to the end of the file once"?
Thank you in advance!

---

### Post by ghostdog74 on 2010-09-01
use awk for this so you can keep a counter/flag to signify found. 

```

awk '/string1/{f=1}END{ if (!f) {print "string2"}}1' file

```
use the best tool for the job.

---

### Post by PryGuy on 2010-09-01
Thanks, pal!

---

### Post by PryGuy on 2010-09-01
Anyway, this construct does not work:
```
sed -i '/string1/!a\string2\' file
```

---

### Post by ghostdog74 on 2010-09-01
> **PryGuy said:**
> Anyway, this construct does not work:
```
sed -i '/string1/!a\string2\' file
```

this will not do what you required. This will supposedly add string2 after every line that string1 is not found.

---

### Post by PryGuy on 2010-09-01
Sorry for being so nasty, but is there a way to do it in sed at all?

---

### Post by ghostdog74 on 2010-09-01
> **PryGuy said:**
> Sorry for being so nasty, but is there a way to do it in sed at all?

I will be nasty as well. I am going to keep asking you, why do you insist on doing that with sed, when you can easily do it with awk (or even other tools like grep)?

```

if grep -q "string1" "$file" ;then
    echo "string2" >> $file
fi

```
this is so much easier !

---

### Post by spjackson on 2010-09-01
> **PryGuy said:**
> Sorry for being so nasty, but is there a way to do it in sed at all?
I'll stick my neck out here. No, it is not possible to do what you want purely in sed. There are many appropriate tools for this task, but sed isn't one of them.

---

### Post by DaithiF on 2010-09-01
well its not what sed was designed for, for sure, but as an exercise in masochism:
```
sed -n 'p;/string1/h;${x;/^$/astring2
}' testfile

```

---

### Post by spjackson on 2010-09-01
> **DaithiF said:**
> well its not what sed was designed for, for sure, but as an exercise in masochism:
```
sed -n 'p;/string1/h;${x;/^$/astring2
}' testfile

```
That's not quite masochistic enough. This fails to output string2 if testfile is empty (0 bytes).

---

### Post by DaithiF on 2010-09-01
true, but as you probably know sed can't do **anything** with 0-byte files.  0 bytes does not constitute a stream, so sed won't even get as far as executing a command.  So if 0-byte files are a possibility then sed would never be the tool to use.

---

### Post by PryGuy on 2010-09-01
Thank you, people!

---

