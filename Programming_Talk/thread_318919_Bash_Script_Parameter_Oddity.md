---
title: "Bash Script Parameter Oddity"
date: 2006-12-14
forum: Programming Talk
---

### Post by fatsheep on 2006-12-14
Is it just me or does for var in "$@" process positional parameters right to left?  Here's why I ask: I've got a program that is meant to process command line arguments.  In my test run, "-" would generate the output "Error!" and "--help" would generate "Help is on the way!".  Now take a look at this output:

> 
ubuntu@ubuntu:~/Desktop/pkgman$ ./argtest4 --help - -
+ ./argtest4 --help - -
Error!
Error!
Help is on the way!


As you can see it's backwards.  --help should have been the first processed but it was the last.  How would I change my script so that positional parameters are processed left to right?  

Source code:
```

#!/bin/bash

for arg in "$@" ; do
	parse_arg=${arg:1}
	case "$parse_arg" in
		-help | h )
			helpflag="1";;
		-info | i )
			infoflag="1";;
		* )
			echo "Error!";;
	esac
done

if [ "$helpflag" = "1" ] ; then
	echo "Help is on the way!"
fi

```

---

### Post by lloyd mcclendon on 2006-12-14
heh

the params are getting processed just fine

take a closer look at the order of your echo statments.  maybe insert an echo ${parse_arg} after you set it to see what i'm getting at

---

### Post by kaamos on 2006-12-14
It is just a logical error.

All the parameters are processed (the for-loop) before the "Help is on the way" print so the errors are printed before that as well. You are looking for something like

```

for a in args
    if a is not valid
        print error and go to next argument
    else
        do something according to a
done

```

---

### Post by fatsheep on 2006-12-14
Aha! ;)  N00bish mistake I know...  Thanks guys. 

-sheep

---

