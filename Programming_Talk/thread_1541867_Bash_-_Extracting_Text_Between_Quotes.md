---
title: "Bash - Extracting Text Between Quotes"
date: 2010-07-29
forum: Programming Talk
---

### Post by glennlh on 2010-07-29
Hi, I have been trying to extract text between quotes using bash and found many other similar questions asked online. I couldn't find one that quite worked for me, so I tried to adapt others but I found sed to complicated and couldn't understand it. I will have a string like this 

```
name='TEXT' date='TEXT' time='TEXT'
```

I want to be able to search extract the text between date=' and '.

Thanks in advanced. Glennlh.

---

### Post by ghostdog74 on 2010-07-29
```

$ echo $string
name='TEXT' date='DATETIME' time='TEXT'
$ echo ${string##*date=\'}
DATETIME' time='TEXT'
$ string=${string##*date=\'}
$ echo ${string%%\'*}
DATETIME


```

---

### Post by glennlh on 2010-07-30
Thanks i've tried the script but it output's

```
name=TEXT
name=TEXT
```

What I need to be able to do is for example enter date and it will output the TEXT from date='TEXT' or I may need the time so it will output TEXT from time='TEXT'.

```
name='TEXT' date='TEXT' time='TEXT'
```

If anyone could give a quick explanation of how it works as well I would be grateful.

Thanks for any help, Glennlh.

---

### Post by ghostdog74 on 2010-07-30
Then you explain more clearly in your first post that you are going to take input.

```

#!/bin/bash

shopt -s nocasematch
printf "Enter: "
read -r string
while read -r line
do
  case "$line" in
   *"$string"* )
      line=${line##*$string=\'}
      echo "${line%%\'*}"
     ;;
  esac
done <"file"



```

output
```

$ cat file
name='TEXT' date='DATE' time='TIME'

$ ./shell.sh
Enter: date
DATE

$./shell.sh
Enter: time
TIME

$ ./shell.sh
Enter: name
TEXT


```

---

### Post by glennlh on 2010-07-30
> **ghostdog74 said:**
> Then you explain more clearly in your first post that you are going to take input.

```

#!/bin/bash

shopt -s nocasematch
printf "Enter: "
read -r string
while read -r line
do
  case "$line" in
   *"$string"* )
      line=${line##*$string=\'}
      echo "${line%%\'*}"
     ;;
  esac
done <"file"



```

output
```

$ cat file
name='TEXT' date='DATE' time='TIME'

$ ./shell.sh
Enter: date
DATE

$./shell.sh
Enter: time
TIME

$ ./shell.sh
Enter: name
TEXT


```
Thank You, works great.

---

