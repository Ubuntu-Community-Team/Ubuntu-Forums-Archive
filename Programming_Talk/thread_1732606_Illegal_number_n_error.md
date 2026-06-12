---
title: "Illegal number n error"
date: 2011-04-18
forum: Programming Talk
---

### Post by madhushubhu on 2011-04-18
Hi
I am facing error in program to find given number is palindrome or not

see my program below

echo "enter the number"
read n
k=n
rev=0
while [$n -ne 0 ]
do
r=n%10
rev=10*rev+r
n=n/10  ------>showing error in this line illegal number 'n'
done


Thanks in advance

---

### Post by manishraj2011 on 2011-04-19
> **madhushubhu said:**
> Hi
I am facing error in program to find given number is palindrome or not

see my program below

echo "enter the number"
read n
k=n
rev=0
while [$n -ne 0 ]
do
r=n%10
rev=10*rev+r
n=n/10  ------>showing error in this line illegal number 'n'
done


Thanks in advance
Here is the corrected code :

echo "enter the number"
read n
k=$n
rev=0
while [ $n -ne 0 ]
do
    r=`expr $n % 10`
    rev=`expr 10 \* $rev + $r`
    n=`expr $n / 10` 
done

if [ $k -eq $rev ]
then
    echo "No. is palindrome"
else
    echo "No. is not a palindrome"
fi

NOTE:- errors in madhushubhu's code:-

1) Shell variable can only be accessed using a '$' sign before variable name.

2) Mathematical expressions can't be evaluated directly, so I have used **expr** command. ( To know more about expr, do **man expr**.

---

