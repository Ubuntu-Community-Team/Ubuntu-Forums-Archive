---
title: "Shell Scripting - Pass a lot of parameters"
date: 2012-08-21
forum: Programming Talk
---

### Post by CrusaderAD on 2012-08-21
Is there anyway I can pass about 12-13 parameters into my shell script? I know I can do something like this:

myprogram "test me" "test this"

$var1 = $1
$var2 = $2

This is only 2, but I'd like to do much more. There seems to be a limit, is there a way around this? Maybe there's a better way to pull data into your command?

---

### Post by CrusaderAD on 2012-08-21
Never mind, figured it out, you can do:

> var1="myvar1" var2="myvar2" myprogram

for as many as you want and call it into the script with $var1 $var2 etc.

---

### Post by snip3r8 on 2012-08-21
I dont know shell scripts well ,but isn't there some sort of array variable?

---

### Post by ofnuts on 2012-08-22
> **CerealCypher said:**
> Is there anyway I can pass about 12-13 parameters into my shell script? I know I can do something like this:

myprogram "test me" "test this"

$var1 = $1
$var2 = $2

This is only 2, but I'd like to do much more. There seems to be a limit, is there a way around this? Maybe there's a better way to pull data into your command?
See the ["shift" builtin]("http://tldp.org/LDP/Bash-Beginners-Guide/html/sect_09_07.html") to access parameters after $9.

You can also avoid a lot of typing using "$*" or "$@" (there are subtle differences between the two) to copy all you input parameters (or, if you used "shift", whatever parameters that haven't been shifted out yet).

---

### Post by Vaphell on 2012-08-22
you can also access $10+ by packaging them in {}
```
$ cat params.sh
#!/bin/bash
echo ${220}
$ ./params.sh {1..300}
220
```
but otherwise "$@"/shift/arrays should be enough to make use of multiple params.

arrays:
```
param=( "$@" )  #store all params in array, indexes starting from 0
# access by index 
echo ${param[22]}
# C-style for loop: print all params, index in 0..[COLOR="Green"]ARRAY_SIZE[/COLOR]-1 range.
for(( i=0; i<[COLOR="Green"]${#param[@]}[/COLOR]; i++ )); do echo $i ${param[$i]}; done
```

---

