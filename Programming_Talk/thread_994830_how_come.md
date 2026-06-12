---
title: "how come??"
date: 2008-11-27
forum: Programming Talk
---

### Post by pcardoso on 2008-11-27
Dear all, 
can any justify the different out come in the following script:


```
function infos
{
        echo "Dear $USER some info $(uptime)"
}

infos2()
{
        echo "Dear $USER some info $(uptime)"
}

echo $(infos)
infos2

```

Output:
```
Dear pcardoso some info 11:08:27 up 1 day, 1:27, 3 users, load average: 0.25, 0.28, 0.27
Dear pcardoso some info  11:08:27 up 1 day,  1:27,  3 users,  load average: 0.25, 0.28, 0.27
```

(* second line as an extra space after "info" and commas *)

Thanks, 
PC.

---

### Post by tang0delta on 2008-11-27
mods delete this post please. I misread the question
[ ]("http://en.wikipedia.org/wiki/Load_%28computing%29")

---

### Post by csilviu on 2008-11-27
Check this one:
```

#!/bin/bash

var="This     is a   text     with    spaces        !!!"
echo $var
echo "$var"

```
Output:
```

silviu@laptop:~$ ./test
This is a text with spaces !!!
This     is a   text     with    spaces        !!!

```
It seems that when echo $var, bash (I guess) is removing extra blank chars.
Whta I'm writing bellow is just some guessing (based on some tests, no documentation found :) )
In you code, you have an extra space at the begining of every line of the "uptime"'s output.
When "echo $(infos)", the output of infos() function is taken as string and outputed (with extra blank chars removed).
When "infos", is just calling that function, text is outputed as is.

As I said before, this is just guessing :)

---

### Post by slavik on 2008-11-27
echo $var makes bash interpret the variable, so you are doing:
echo This     is a   text     with    spaces        !!!

since white spaces delimit arguments, the shell throws them out and gives a list of stuff to echo. the list is the individual words.

the second one cause it to be quoted and passed as a since argument.

also, if you notice, the output of uptime is actually includes the extra spaces you see. :)

---

### Post by pcardoso on 2008-11-27
> **slavik said:**
> echo $var makes bash interpret the variable, so you are doing:
echo This     is a   text     with    spaces        !!!

since white spaces delimit arguments, the shell throws them out and gives a list of stuff to echo. the list is the individual words.

the second one cause it to be quoted and passed as a since argument.

also, if you notice, the output of uptime is actually includes the extra spaces you see. :)


I agree with you, this is certanly the answer.
thkx,
PC.

---

