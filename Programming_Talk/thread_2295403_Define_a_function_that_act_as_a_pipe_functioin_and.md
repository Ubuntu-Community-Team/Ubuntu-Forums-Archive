---
title: "Define a function that act as a pipe functioin and argument function  at the same tim"
date: 2015-09-18
forum: Programming Talk
---

### Post by CkDGTAT on 2015-09-18
Hi,

I need to define a lot bash functions that would work  both as a **pipe function **and an **argument function**.

What is the most compact and direct way of doing it?

Thank you

PS:

Example:

**myfunction1 **is *pipe function:*

```

cat myfile | myfunction1

```


**myfunction2 **is *argument function:*

```

myfunction myfile

```

---

### Post by Bucky Ball on 2015-09-18
Would help if you could tell us what the object of the project is. What is the end result you are looking for?

---

### Post by CkDGTAT on 2015-09-18
Hi,

I am defining bash functions in order to gain time with the cli.

Is this example the most adequate way of doing it or would you propose something else:

```

$declare -f awk_1

awk_print_1 () {
if [[ -n $@ ]]
then
echo $@ | awk '{ print $1 }'
else

    while read i
    do
        echo $i | awk '{ print $1; }'
    done

fi
}







```

---

### Post by Bucky Ball on 2015-09-19
*Thread moved to **Programming Talk**.*

---

### Post by Vaphell on 2015-09-21
```
#!/bin/bash


>&2 printf '%s\n' 'params:' "$@"

if [[ -t 1 ]]
then
    >&2 echo "stdout to tty"
else
    >&2 echo "stdout redirected somewhere"
fi

if [[ $(readlink /proc/$$/fd/0) =~ ^pipe:.* ]]
then
    >&2 echo "stdin from pipe"
    while read -r ln
    do
        >&2 echo "$((++i)) $ln [$*]"
    done
fi
```

note that in this example everything is printed out to stderr so the redirection of stdout to a black hole doesn't silence the script
result

```
$ ./pipe_redir_test.bash a b c
params:
a
b
c
stdout to tty
$ ./pipe_redir_test.bash a b c > /dev/null
params:
a
b
c
stdout redirected somewhere
$ echo $'a\nb\nc' | ./pipe_redir_test.bash 1 2 3 > /dev/null
params:
1
2
3
stdout redirected somewhere
stdin from pipe
1 a [1 2 3]
2 b [1 2 3]
3 c [1 2 3]

```

---

