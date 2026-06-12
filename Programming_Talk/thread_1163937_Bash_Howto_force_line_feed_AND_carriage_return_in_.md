---
title: "Bash: Howto force line feed AND carriage return in script?"
date: 2009-05-19
forum: Programming Talk
---

### Post by Lampi on 2009-05-19
I do have a bash script with several echo commands called like this:

echo -n "Hello World"

How do I format the echo line to force line feed **AND** carriage return after each command?

At the moment the echo output looks like this:

```
Hello World
    Hello World
       Hello World
           Hello World
```
not what I had in mind...

Can I somehow combine /n oder /r to force line feed and carriage return in scripts or can I use ANSI / escape sequences?

---

### Post by howlingmadhowie on 2009-05-19
why are you passing the -n flag to echo?

---

### Post by ghostdog74 on 2009-05-19
use printf

---

### Post by cdenley on 2009-05-19
```

echo -e "line1\r\nline2"

```

You shouldn't need a carriage return if the script is run on Linux. Several echo lines wouldn't result in each line being further to the right. If you use the "-n" option, they will all be on one line, though.

---

