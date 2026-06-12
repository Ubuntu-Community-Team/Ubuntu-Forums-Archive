---
title: "running a program in the background in linux"
date: 2014-03-26
forum: New to Ubuntu
---

### Post by aashik2 on 2014-03-26
I need to run a program in the background . I know that using '&' after a command runs the command in the background.  In the give program:-
  ```
#!/bin/bash
echo amt of time delay nsec
read nano
echo amt of time delay in sec
read sec
echo no.of times
read i
while [ $i -ne 0 ]
do
./nanosleep $sec $nano
./schello
i=$[i-1]
done
```  I have a few data that i get from the user. Is there a way I can run  the program in background? i.e, while calling the program can i also  specify the data required(like nano, sec,i) as arguments or through some  other way?

---

### Post by TheFu on 2014-03-26
There are a few options.
* Get the inputs from files, not interactively.
* Call the long-running parts from a different script - that runs in the background. That would probably be the loop and everything inside it.
* Push long running tasks onto a queue manager - like TaskSpooler
Or
* after the script starts, use the built-in process management inside almost every shell to stop the process and put it into the background.   cntl-z, then type 'bg'  - the bad part of this is that output will be sent to the terminal and will interrupt any other tasks ... including running CLI programs.

---

### Post by steeldriver on 2014-03-26
> **aashik2 said:**
> while calling the program can i also  specify the data required(like nano, sec,i) as arguments

Yes - if you call the script as

```
./myscript 123 456
```

then the values (123 and 456) will be available as *positional parameters* $1 and $2 inside your script

---

### Post by 7sbaV8Kt5PTh on 2014-03-26
To background a script, you can use 'nohup'.  so, paraphrasing steeldriver:  nohup ./myscript 123 456
then do a "ps -ef | grep myscript" to make sure it is running.

---

### Post by Navneet_Kumar on 2014-03-27
Along with using & after the command,using 'nohup' will be beneficial...........and you can view that your program is successfully by typing the command 'top'.......

---

