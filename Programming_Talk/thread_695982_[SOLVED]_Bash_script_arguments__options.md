---
title: "[SOLVED] Bash script arguments / options"
date: 2008-02-13
forum: Programming Talk
---

### Post by Dr Small on 2008-02-13
First off, I don't know the proper names for this, so that hasn't helped any of my search results.

Basically I would like to write a bash script that I use at the command line like:
```
./filename <input1> <input2>
```
and or (for a different setting:
```
./filename --option1 --option2
```

But I don't know how to do any of it, or what it's proper names are...

Dr Small

---

### Post by Jussi Kukkonen on 2008-02-13
script name is $0, and arguments are $1, $2, $3.... 
$* = all arguments, $# = number of arguments

```
jku@vili:~$ cat test.sh 
echo $#
echo $*
echo $2
jku@vili:~$ ./test.sh a b c
3
a b c
b

```

---

### Post by Dr Small on 2008-02-13
Thanks :)
That's exactly what I was looking for, and it was helpful!

Dr Small

---

### Post by Dr Small on 2008-02-13
Thanks :)
That's exactly what I was looking for, and it was helpful!

Dr Small

---

### Post by stroyan on 2008-02-13
You should look at the 'getopt' command.
It exists to help in parsing options to scripts.
There is also a bash 'getopts' built-in.
But the getopt command can handle the long --option form.
The getopts built-in handles only single-character options.

---

### Post by slavik on 2008-02-13
> **Jussi Kukkonen said:**
> script name is $0, and arguments are $1, $2, $3.... 
$* = all arguments, $# = number of arguments

```
jku@vili:~$ cat test.sh 
echo $#
echo $*
echo $2
jku@vili:~$ ./test.sh a b c
3
a b c
b

```
$@ is also all arguments but different from $* as $@ concatenates them into a single argument :)

---

### Post by Arvid Requate on 2011-10-07
> **stroyan said:**
> There is also a bash 'getopts' built-in.
[...]
The getopts built-in handles only single-character options.

The Bash builtin getopts function can be used to parse long options by putting a dash character followed by a colon into the optspec. For an example script see:

[http://stackoverflow.com/questions/402377/using-getopts-in-bash-shell-script-to-get-long-and-short-command-line-options/7680682#7680682](http://stackoverflow.com/questions/402377/using-getopts-in-bash-shell-script-to-get-long-and-short-command-line-options/7680682#7680682)

---

### Post by nothingspecial on 2011-10-07
This old thread has gone mouldy.

Time for reburial.

---

