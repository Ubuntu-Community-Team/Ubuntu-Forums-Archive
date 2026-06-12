---
title: "Help with Awk (using Bash)"
date: 2012-06-29
forum: Programming Talk
---

### Post by guangyan on 2012-06-29
I've been trying to write a script in bash that can print out the list of subdirectories in the current directory, then running the 'wc' command. The script works fine when I do:

ls -l | awk '{print $8}' | while read line; 
do
x=$line
z=$(ls $line | wc)
echo  $x $z
done

But when I replaced "echo $x $z" with :

awk '{ printf "%-10s %s\n", $x, $z }'

the script doesn't work anymore. It just prints two identical columns, as if the variable $z was replaced with $x. Any help on making the awk command work?

Thanks,
Guang

---

### Post by mainmeister on 2012-06-29
have you tried breaking the printf into 2 statements? Only place the '\n' on the second one.

---

