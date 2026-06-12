---
title: "How can we do this in bash console"
date: 2023-08-03
forum: New to Ubuntu
---

### Post by alexbaqua on 2023-08-03
Dear all,
I want to direct output of a bash command to another command. Instance: I have 1.txt 2.txt 3.txt 4.txt in a specific folder. i will take output of all file and direct this output in an other program. For example find ./Folder | cat $1. How can we do this without using bash script or programatically
Try to define the operation the $1 would symbolize the parameter of output that was directed another program by the user.
I tested this script but not satisfying
find>o.txt
while read line;do
    cat "$line"
done<o.txt

---

### Post by SeijiSensei on 2023-08-03
Use a pipe

```
cat file1.txt | some_other_program
```

Stdout from cat will be sent to stdin on some_other_program.

---

### Post by Holger_Gehrke on 2023-08-04
@SeijiSensei: I think what alexbaqua wants is more in the line of a command line substitution ...

```

cat $(find . -type f)

```
will execute 'find' to find normal files (no directories,symlinks,devices, FIFOs or sockets) in the current directory and its subdirectories and put the filenames into the command line as arguments to 'cat'.

Also find has an action '-exec' which allows you to give a command to be executed on each and every found file. Read 'man find' for details.

Holger

---

