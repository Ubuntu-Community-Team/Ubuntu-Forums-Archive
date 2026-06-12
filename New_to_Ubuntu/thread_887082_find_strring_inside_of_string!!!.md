---
title: "find strring inside of string!!!"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by just_linux on 2008-08-11
I have some strings in variable, and I want to know if that string has "24" or space 
How can I search through the string?
:lolflag:
ALSO, I need the complite list of if , for, while compare thing ( like -lt -gt,  and what is the rest???? 

Also, :guitar:
how can I have a switch in shell programming :guitar:
Thanks

---

### Post by aimpau on 2008-08-12
go to your terminal and type

```

man find

```

---

### Post by niteshifter on 2008-08-12
Hi,

The find command won't work, he's looking to pattern match inside a shell variable, not to or via an object in the file system.

Look at this  [thread]("http://www.linuxquestions.org/questions/programming-9/bash-search-for-a-pattern-within-a-string-variable-448022/") (linuxquestions.org). Post #3 and #5.

---

### Post by unutbu on 2008-08-12
> 
I need the complite list of if , for, while compare thing ( like -lt -gt, and what is the rest????

-lt, -gt, etc. are part of the test command. The brackets [ ... ] are an alternate way of running test. So if you type
```

help test
help [
```

in a terminal running a bash shell, you get documentation on the bash command 'test'. You can get a handy complete list that way.

> 
Also, how can I have a switch in shell programming 

```

help case

```
Go to any of the scripts in /etc/init.d/. At the end of each of these scripts there is an example of the use of the case statement.

---

