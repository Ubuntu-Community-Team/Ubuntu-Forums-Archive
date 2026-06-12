---
title: "bash question - double parentheses within case statement"
date: 2011-12-04
forum: Programming Talk
---

### Post by linuxed on 2011-12-04
I have a bash script that contains a line with double parentheses within a case statement.  The script returns an error any time it is run stating that ";;" were expected instead of ")".  How can I use double parentheses within a case statement?
```

case "$1" in
        start)
        VAR1=($(<"SOMETHING"))
        ;;
esac

```

---

### Post by Vaphell on 2011-12-04
do you have a hashbang line in your script?
because the script with explicit bash hashbang works just fine when called by **./script**, only when i invoke the script with **sh script** i get your error

---

### Post by linuxed on 2011-12-04
I have a main script that calls numerous other bash scripts.  For example, script2 is called by script1.  Both contain "#!/bin/sh" as the first line.  I just type ./script1 to run the scripts.  I should also probably mention that I'm running XFCE.  Not sure if that makes any difference.

**script1**
```

#!/bin/sh

script2

```

**script2**
```

#!/bin/sh

case "$1" in
        start)
        VAR1=($(<"SOMETHING"))
        ;;
esac

```

---

### Post by SevenMachines on 2011-12-04
the default shell is dash not bash
```
$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 May  3  2011 /bin/sh -> dash
```
So avoid bashisms
```
$ sudo apt-get install devscripts
$ checkbashisms ./script2 
possible bashism in ./script2 line 5 ('$(< foo)' should be '$(cat foo)'):
        VAR1=($(<"SOMETHING"))
```

---

