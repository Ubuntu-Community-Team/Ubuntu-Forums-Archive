---
title: "getopts ignore errors"
date: 2014-05-10
forum: Programming Talk
---

### Post by Sparkye on 2014-05-10
Hello,
is there a way how to prevent getopts from exiting when an unexpected option is found?
code:
while getopts "a:b:c:d:" OPT; do
  case $OPT in
     a) #do something
.
.
.
     \? echo UNEXPECTED OPTION FOUND
 esac

when I run ./myscript -a opt1 -e opt2 -b opt3
it prints UNEXPECTED OPTION FOUND, but does not process the -b option. Is there a way how to force getopts to keep processing even after an unexpected option? E.g. if I wont to precess it by myself or when I want to ignore the unknown options?
Thanks in advance.

---

### Post by Vaphell on 2014-05-11
[http://wiki.bash-hackers.org/howto/getopts_tutorial](http://wiki.bash-hackers.org/howto/getopts_tutorial)

start the option string with :

---

### Post by Sparkye on 2014-05-13
> **Vaphell said:**
> [http://wiki.bash-hackers.org/howto/getopts_tutorial](http://wiki.bash-hackers.org/howto/getopts_tutorial)

start the option string with :

I have already tried that, but it only suppresses getopts from error output but still ends the getopts.
in this case:

getopts ":a:b:c:"
.
.
.

$ ./myscript -a first -G second -b third
it processes -a correctly, but not -b as I wanted. All i want is to skip the "-G second" and continue to next argument (-b)

---

### Post by Vaphell on 2014-05-13
It's kind of tricky problem. How is the script supposed that not only it should treat the unexpected arg as a switch not as a non-option arg, but also that it should skip its followup?

I think you need to either call getopts again, but on a subset of args

```
#!/bin/bash

echo ==1==
while getopts ":a:b:" opt
do
  echo "$opt: $OPTARG ($OPTIND)"
done

echo ==2==
while getopts ":a:b:" opt "${@:$((OPTIND-2))}"
do
  echo "$opt: $OPTARG ($OPTIND)"
done
```

```
$ ./getopts.bash -a 1 -x 2 -b 3
==1==
a: 1 (3)
?: x (4)
==2==
b: 3 (6)
```


or write your own solution by hand, eg

```
while (( $# ))
do
    case $1 in
    -[ab]) echo ${1#-}=$2; shift;;
    -*) echo "$1 ???"; shift;;
     *) echo "non-opt arg: $1";;
    esac
    shift
done
```

---

### Post by Sparkye on 2014-05-13
> **Vaphell said:**
> It's kind of tricky problem. How is the script supposed that not only it should treat the unexpected arg as a switch not as a non-option arg, but also that it should skip its followup?

I think you need to either call getopts again, but on a subset of args

```
#!/bin/bash

echo ==1==
while getopts ":a:b:" opt
do
  echo "$opt: $OPTARG ($OPTIND)"
done

echo ==2==
while getopts ":a:b:" opt "${@:$((OPTIND-2))}"
do
  echo "$opt: $OPTARG ($OPTIND)"
done
```

```
$ ./getopts.bash -a 1 -x 2 -b 3
==1==
a: 1 (3)
?: x (4)
==2==
b: 3 (6)
```


or write your own solution by hand, eg

```
while (( $# ))
do
    case $1 in
    -[ab]) echo ${1#-}=$2; shift;;
    -*) echo "$1 ???"; shift;;
     *) echo "non-opt arg: $1";;
    esac
    shift
done
```

Yeah, I will probably try to use while - do - done instead
thanks a lot

---

