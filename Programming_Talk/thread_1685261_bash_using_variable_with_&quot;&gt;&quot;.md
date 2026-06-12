---
title: "bash: using variable with &quot;&gt;&quot;"
date: 2011-02-10
forum: Programming Talk
---

### Post by KIAaze on 2011-02-10
Hi,

I had some problems with a script recently and narrowed it down to this:
```
#!/usr/bin/env bash
set -eux
export FOO="A > B"
cat $FOO

```

When I run it, I get:
```
+ export 'FOO=A > B'
+ FOO='A > B'
+ cat A '>' B
hello
cat: >: No such file or directory
cat: B: No such file or directory

```
i.e. the problem is that it tries to run "cat A '>' B" instead of "cat A > B".

Is there a solution other than splitting the arguments in 2, one for the left side of '>' and one for its right side and writing:
cat $VAR1 > $VAR2 ?
Why does it add single quotes?

---

### Post by Cheesehead on 2011-02-10
I don't think you can cat a variable.
instead of ```
cat $FOO
```
try one of```

echo "$FOO"
echo "$FOO" > "$BAR"
printf "${FOO}\n" > "$BAR"
```

---

### Post by sisco311 on 2011-02-10
After the parameter expansion the expression is not reevaluated. The value of the variable is passed as an argument to cat.

You have to use eval:
```
eval cat $FOO
```

See:
```
man bash | less +/"eval \[arg ...\]"
```

---

### Post by KIAaze on 2011-02-10
> **Cheesehead said:**
> I don't think you can cat a variable.

It's a text file. The names A and B were perhaps not well chosen. But I was just trying to reduce the problem to the minimum.

> **sisco311 said:**
> After the parameter expansion the expression is not reevaluated. The value of the variable is passed as an argument to cat.

You have to use eval:
```
eval cat $FOO
```

See:
```
man bash | less +/"eval \[arg ...\]"
```

Thanks. That works indeed. :)
I'm still trying to figure out why the script worked that way (with > inside the variable) before I made some changes. It might be related to the way I called it too.

Interesting "man bash | less+/*" trick as well. :)

---

