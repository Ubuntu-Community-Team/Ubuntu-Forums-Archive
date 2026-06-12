---
title: "A shell scripting help...."
date: 2009-07-21
forum: Programming Talk
---

### Post by veda87 on 2009-07-21
i have written a small piece of code inorder to add several users.....```
#! /bin/bash

num=0

echo -n "Enter the number of users: "
read num
while [ $num -gt 0 ];
do
        echo -n "Enter the user name: "
        read user
        echo -n "Password: "
        read -s password

        useradd $user
        echo $password > passwd --stdin $user
        $num = $(($num - 1))
        echo $num
done

```When i executed this code... it prompted me like....```
veda@veda-desktop:~/myhand$ ./useradd 
Enter the number of users: 3
Enter the user name: qwe
Password: ./useradd: line 16: 3: command not found
3
Enter the user name: qwe
Password: ./useradd: line 16: 3: command not found
3
Enter the user name: qwe
Password: ./useradd: line 16: 3: command not found
3
Enter the user name: qwe
Password: ./useradd: line 16: 3: command not found
3
Enter the user name: qwe
Password: 
veda@veda-desktop:~/myhand$ vi useradd

```What syntax would be suitable for this...
Thanks in advance...

---

### Post by apoth on 2009-07-21
This should work:

```
#!/bin/bash

num=0

echo -n "Enter the number of users: "
read num
while [ $num -gt 0 ];
do
        echo -n "Enter the user name: "
        read user
        echo -n "Password: "
        read -s password

        useradd $user
        echo $password > passwd --stdin $user
        num=$(($num-1))
        echo $num
done
```

---

### Post by lavinog on 2009-07-21
> **veda87 said:**
> i have written a small piece of code inorder to add several users.....```

        $num = $(($num - 1))

```When i executed this code... it prompted me like....```
veda@veda-desktop:~/myhand$ ./useradd 
Enter the number of users: 3
Enter the user name: qwe
Password: ./useradd: line 16: 3: command not found
3

```

When assigning a value to a variable don't put the $ sign in front of the variable
that line reads
```

3=2

```

---

### Post by apoth on 2009-07-21
> **lavinog said:**
> When assigning a value to a variable don't put the $ sign in front of the variable
that line reads
```

3=2

```

I think the line reads 3 = 2, so the space between the 3 and the = causes bash to interpret the 3 as a command. I think the $ sign is actually required as part of evaluating the expression as integer arithmetic, otherwise the while loop fails?

---

