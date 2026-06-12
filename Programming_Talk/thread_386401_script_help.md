---
title: "script help"
date: 2007-03-17
forum: Programming Talk
---

### Post by mozkaynak on 2007-03-17
I try to write very very basic script using only one if statement. However, it does not work. I tried to run in on the terminal manually and I got the same error message (command not found). Which command is it talking about? 
can anyone tell me what is wrong?

the terminal output is:

> 
mozkaynak@ozkaynak:~$ read choice
1
mozkaynak@ozkaynak:~$ if ["$choice"="1"] ;then
> ls
> else
> echo else
> fi
bash: [1=1]: command not found
else
mozkaynak@ozkaynak:~$ 


Thanks alot in advance.....

---

### Post by ghostdog74 on 2007-03-17
try this:

```

...
if [ $choice -eq 1 ];then
...

```

---

### Post by tomchuk on 2007-03-17
Your problem was the lack of space after '[' and before ']'. '[' is actually a program (or shell builtin) and  '"$choice" = "1" ]' are its arguments.

Your original test is better than ghostdog74's. If the user enters "1 0", [ "$choice" = "1" ] will work and evaluate to false, where as [ $choice -eq 1 ] will not work and fail with "bash: [: too many arguments" as the "1 0" will be parsed as 2 separate arguments to '['

So it should be:```

...
if [ "$choice" = "1" ] ;then
...

```

---

### Post by ghostdog74 on 2007-03-17
you are right in this case,since OP is comparing only equality. however, OP should take note that comparing numbers still require the use of eq,lt,gt etc...

---

