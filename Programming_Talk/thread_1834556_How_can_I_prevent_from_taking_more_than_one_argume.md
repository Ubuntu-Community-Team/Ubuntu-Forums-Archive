---
title: "How can I prevent from taking more than one argument in a bash script"
date: 2011-08-27
forum: Programming Talk
---

### Post by Icche Ghuri on 2011-08-27
I want to make a simple bash script, in which I want to take just "one" argument with --arg command. Here is my script,

```
#!/bin/bash

if [ "$1" == --arg1 ]; then
	echo "This is arg1"

elif [ "$1" == --arg2 ]; then
	echo "This is arg2"

elif [ "$1" == --arg2 ]; then
	echo "This is arg3"

else
	echo "Please use arg1, arg2 or arg3"

fi
```

If I give a command like this
```
program --arg1 --arg2
```
it gives me "Please use arg1, arg2 or arg3". But if I give,
```
program --arg1 arg3
```
it gives me "This is arg1". In this case also I want to echo in the last else condition. How can I do that?

---

### Post by Bachstelze on 2011-08-27
Use the special variable $#, which is the number of arguments.

---

### Post by Icche Ghuri on 2011-08-27
> **Bachstelze said:**
> Use the special variable $#, which is the number of arguments.

Thanks a lot. I found this script from [this link]("http://www.linuxweblog.com/bash-argument-numbers-check"), which solved my problem:

```
# Check for proper number of command line args.

EXPECTED_ARGS=1
E_BADARGS=65

if [ $# -ne $EXPECTED_ARGS ]
then
  echo "Usage: `basename $0` {arg}"
  exit $E_BADARGS
fi
```

---

