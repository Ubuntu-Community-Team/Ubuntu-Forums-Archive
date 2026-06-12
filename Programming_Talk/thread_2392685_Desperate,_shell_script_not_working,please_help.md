---
title: "Desperate, shell script not working,please help"
date: 2018-05-23
forum: Programming Talk
---

### Post by 13bubus on 2018-05-23
Hello everybody,
Im trying to get this script working but what I get is: 
14: Syntax error: "(" unexpected (expecting "fi").

Hope you guys can solve my problem...

Thanks in advance.


Here is the script:

```

#!/bin/bash
#========================================
#Eb  
#Date:  15/5/2018
#Nombre:ID:Telefono:Direccion:DOB:Departamento:Salario
#
#=========================================
filein="proyecto3.csv"
IFS=$'\n'
if [ ! -f "$filein" ]
then
echo "Cannot find file $filein"
else
  groups=(`cut -d: -f 6 "$filein" | sed 's/ //'`)
  fullnames=(`cut -d: -f 1 "$filein"`)
  userid=(`cut -d: -f 2 "$filein"`)
  usernames=(`cut -d: -f 1 "$filein" | tr [A-Z] [a-z] | awk '{print substr($1,1,1) $2}'`)
fi
for group in ${groups
[*]}
do
grep -q "^$group" /etc/group ; let x=$?
if [ $x -eq 1 ]
then
groupadd "$group"
fi
done
  x=0
  created=0
for user in ${usernames
[*]}
do
useradd -n -c ${fullnames[$x]} -g "${groups[$x]}" $user 2> /dev/null
if [ $? -eq 0 ]
then
let created=$created+1
fi
echo "${usernames[$x]}" | passwd --stdin "$user" > /dev/null
echo "Complete. $created accounts have been created."
fi

```

---

### Post by QIII on 2018-05-23
Hello!

Have you consulted with your instructor or your classmates?

---

### Post by 13bubus on 2018-05-23
> **QIII said:**
> Hello!

Have you consulted with your instructor or your classmates?

I don't go to school and honestly I do not see the usefulness of your answer.

---

### Post by kerry_s on 2018-05-24
all wrong, you can't just add on any which way.

read up on> if elif else<- [https://www.google.com/search?client=ubuntu&channel=fs&q=if+elif&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=if+elif&ie=utf-8&oe=utf-8)

---

### Post by QIII on 2018-05-24
> **13bubus said:**
> I don't go to school and honestly I do not see the usefulness of your answer.

That was not an answer.  It was a question, asked by a Forum Admin for a purpose.

---

### Post by mohicann on 2018-06-03
```

#!/bin/bash
#========================================
#Eb  
#Date:  15/5/2018
#Nombre:ID:Telefono:Direccion:DOB:Departamento:Salario
#
#=========================================
filein="proyecto3.csv"
IFS=$'\n'
if [ ! -f "$filein" ]
then
echo "Cannot find file $filein"
else
  groups=(`cut -d: -f 6 "$filein" | sed 's/ //'`)
  fullnames=(`cut -d: -f 1 "$filein"`)
  userid=(`cut -d: -f 2 "$filein"`)
  usernames=(`cut -d: -f 1 "$filein" | tr [A-Z] [a-z] | awk '{print substr($1,1,1) $2}'`)
fi
for group in ${groups
[*]}
do
grep -q "^$group" /etc/group ; let x=$?
if [ $x -eq 1 ]
then
groupadd "$group"
fi
done
  x=0
  created=0
for user in ${usernames
[*]}
do
useradd -n -c ${fullnames[$x]} -g "${groups[$x]}" $user 2> /dev/null
if [ $? -eq 0 ]
then
let created=$created+1
fi
echo "${usernames[$x]}" | passwd --stdin "$user" > /dev/null
echo "Complete. $created accounts have been created."

```

should work better. But the previous answers are relevant, it was VERY easy to find out based on the if-else-then logic, except if you are ABSOLUTELY not at ease with computing.

---

