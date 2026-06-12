---
title: "potentally noobish bash problem"
date: 2010-11-01
forum: Programming Talk
---

### Post by Someone uk on 2010-11-01
i am trying to run this script that compares the 2 parameters and evalueates which one is larger
i keep getting "syntax error: unexpected end of file"
(i am using redhat if that makes any diffrence)
```

#!/bin/sh
if (@1 > @2) then
echo first number is larger than the second
if (@2 > @1) then
echo second number is larger than first
if (@1 == @2) then
echo the 2 numbers are equal
endif

```

---

### Post by Vox754 on 2010-11-01
> **Someone uk said:**
> i am trying to run this script that compares the 2 parameters and evalueates which one is larger
i keep getting "syntax error: unexpected end of file"
(i am using redhat if that makes any diffrence)
```

#!/bin/sh
if (@1 > @2) then
echo first number is larger than the second
if (@2 > @1) then
echo second number is larger than first
if (@1 == @2) then
echo the 2 numbers are equal
endif

```

Lol!

Your code *might* be correct, but that depends on the specific shell you are using, certainly it is not correct in POSIX shell or in the widely used Bash.
```

#!/bin/sh
# POSIX shell
if [ $1 -gt $2 ]
then
    echo "first number is larger than the second"
elif [ $2 -gt $1 ]
then
   echo "second number is larger than first"
elif [ $1 -eq $2 ]
then
   echo "the 2 numbers are equal"
fi

```

```

#!/bin/bash
if [[ $1 > $2 ]]
then
    echo "first number is larger than the second"
elif [[ $2 > $1 ]]
then
   echo "second number is larger than first"
elif [[ $1 == $2 ]]
then
   echo "the 2 numbers are equal"
fi

```

Always use Bash, it is powerful and widely available in Linux. Only use POSIX shell when you know the target system may not have Bash, and you need to maintain strict compatibility among systems.

So, learn the correct syntax for your shell. Each shell is a programming language of its own, the same way Perl code won't run with a Python interpreter.

---

