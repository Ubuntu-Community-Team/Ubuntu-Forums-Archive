---
title: "weird script problem"
date: 2007-03-08
forum: Programming Talk
---

### Post by helmet on 2007-03-08
script efficiency aside, when i run this

```
ps aux | grep apache | awk "/$1$/ { print\$2 } " | tr '\n' ',' | sed -r -e 's/,$/\n/g'
```

on the command line i get a nice list of PIDS seperated by comma's which is what i want. now when i run this

```
top -p `ps aux | grep apache | awk "/$1$/ { print\$2 } " | tr '\n' ',' | sed -r -e 's/,$/\n/g'`
```

to make top use that list of pids, it runs as if it skips the awk section of of things, and I get the original stuff with the commas replacing \n except at the end. wtf

is there something the ` ` doesn't like about the " " in the awk part of things? can somebody suggest a better way of doing this?

i just want to run a script to monitor all of apaches pids

even better, can somebody point me to something to realtime monitor a process (apache) for memory usage, processor time, etc and put it in a graph or something?

---

### Post by po0f on 2007-03-08
helmet,

`**pidof**' returns a space-separated list of PIDs given a process name, maybe this will work better for you?

[EDIT]

Example usage:

```
$ **pidof apache**
1234 5678 9012
$
```

---

### Post by Mr. C. on 2007-03-08
Simpler solution aside for the moment, there are a number of problems with your script.

First, what do you believe this does? :

```
awk "/$1$/ { print\$2 } "
```

And what do you believe this does: ?
```
echo `echo "$1"`
```
Compare this to your ` .... awk "/$1/" .... `

MrC

---

### Post by helmet on 2007-03-09
honestly i have no clue what the awk stuff does. i'm not proficient with awk at all i just googled because I knew awk could do what i wanted, found that, and strung all those pipes together to form the command and it output what i wanted


this does what i want it to now...

```
top -p `pidof apache2 | tr ' ' ','`
```

edit: thanx po0f for the info :)

---

### Post by Mr. C. on 2007-03-09
That is a much cleaner approach.

MrC

---

