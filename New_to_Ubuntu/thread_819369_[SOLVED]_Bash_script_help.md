---
title: "[SOLVED] Bash script help"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by Tornam on 2008-06-05
I'm trying to write a Bash script to copy files 'sim1b.txt' to 'sim20b.txt' from one location to another, renaming them 'sim11b.txt' to 'sim30b.txt'.

Assuming the folder names etc. are correct, how do I get this to work?  I tried the following without success:

```


for (( i=1 ; i<=20 ; i++ ))

do

j=i+10

cp "/folder1/sim"$i"b.txt" "/folder2/sim"$j"b.txt"

done


```


Any help is much appreciated.  Thanks!

---

### Post by turinglabs on 2008-06-05
You've got quotes within quotes - you need to explicitly separate the shell variables from the rest of the string with curly braces. You'll also need (()) syntax for the addition. This should work:

```

for (( i=1 ; i<=20 ; i++ ))

do

(( j=i+10 ))

cp "/folder1/sim${i}b.txt" "/folder2/sim${j}b.txt"

done

```

---

### Post by Tornam on 2008-06-06
Excellent, thank you!!

---

