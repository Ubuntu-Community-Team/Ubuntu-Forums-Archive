---
title: "Write a script that checks if an interface is up?"
date: 2011-08-14
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-08-14
Hello all, 

I'm just trying to hone my skills in bash and come up with random scripts to make. Basically i want to make a script that tells me whether and interface is up or not. 

I have been trying all sorts of different formations of code but i can't get it right. 

Here is the code i have so far. 

```
#!/bin/bash
t1='ifconfig | grep eth0'
t2='ifconfig eth0 | grep eth0'

if [ "$t1" = "$t2" ]; then
  echo "eth0 up"
else
  echo "eth0 down"
fi

exit

```Even though the interface is up it still replies that it is down. Any ideas guys? 

Thanks, 
SlashWannabe94

---

### Post by mikewhatever on 2011-08-14
```
#!/bin/bash
t1=$(ifconfig | grep -o eth0)
t2='eth0'

if [ "$t1" = "$t2" ]; then
  echo "eth0 up"
else
  echo "eth0 down"
fi

exit

```

... seems to work.;)

---

### Post by slashwannabe94 on 2011-08-14
that works :D Many thanks :)

SlashWannabe94

---

### Post by lavinog on 2011-08-15
If you would like to know what was wrong:

```
#!/bin/bash
t1='ifconfig | grep eth0'
t2='ifconfig eth0 | grep eth0'

if [ "$t1" = "$t2" ]; then
  echo "eth0 up"
else
  echo "eth0 down"
fi

exit

```

```

# original code
$ t1='ifconfig | grep eth0'
$ echo $t1
ifconfig | grep eth0

# replaced single quotes with backticks
$ t1=`ifconfig | grep eth0`
$ echo $t1
eth0 Link encap:Ethernet HWaddr 00:1f:d0:XX:XX:XX

# replaced backticks with $()
$ t1=$(ifconfig | grep eth0)
$ echo $t1
eth0 Link encap:Ethernet HWaddr 00:1f:d0:XX:XX:XX

```

Backticks are what you were wanting to use originally.  The backtick is the key next to the number 1 on most keyboards.

The backtick expression is the old way of doing command substitution, and is not very efficient as it creates a new shell for each command.
The $() form of command substitution is better for a number of reasons.  One reason is readability...as you may have just found out ;)

---

