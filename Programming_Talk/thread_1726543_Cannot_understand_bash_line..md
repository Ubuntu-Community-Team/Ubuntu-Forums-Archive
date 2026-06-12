---
title: "Cannot understand bash line."
date: 2011-04-11
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-04-11
Hello everyone, I have came across a line of code that i do not understand. Can anyone tell me what is going on when this line is executed. 

[[ $? -eq 0 ]] || { echo "Failed to install SSMTP, exiting..."; exit 1; }

Thanks SlashWannabe94

---

### Post by v8YKxgHe on 2011-04-11
The variable "$?" will hold the status/exit code of the last executed command. "-eq" stands for equals, "[[" is a shell keyword that allows you to do conditional tests.

Essentially if the status/exit code does not equal 0, echo that message. A more human readable way would have been:

```
command || echo "Failed ..."
```

---

### Post by slashwannabe94 on 2011-04-11
I see :) 
I think i understand. So correct me if i am wrong but this is my current understanding; the code marked in blue is the same as if [[ $? -lt 1 ]] ?

cat /etc/foo
[COLOR=Blue]
if [ $? -lt 1 ][/COLOR]; 
  then
    echo "Return Value of cat /etc/foo: $?"
  else 
    echo "Program Failed..."
fi

exit 


Thanks, 
SlashWannabe94

---

### Post by sisco311 on 2011-04-11
Check out:
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

[s]
```
command1 && command2 || command3
```
is the equivalent of:
```
if command1
then
  command2
else
  command3
fi
```[/s]

---

### Post by v8YKxgHe on 2011-04-12
> **sisco311 said:**
> Check out:
[http://mywiki.wooledge.org/BashGuide/TestsAndConditionals](http://mywiki.wooledge.org/BashGuide/TestsAndConditionals)

```
command1 && command2 || command3
```
is the equivalent of:
```
if command1
then
  command2
else
  command3
fi
```

No it's not, you really should never do that. See (ironically from the same site ...) [http://mywiki.wooledge.org/BashPitfalls#cmd1_.26.26_cmd2_.7C.7C_cmd3](http://mywiki.wooledge.org/BashPitfalls#cmd1_.26.26_cmd2_.7C.7C_cmd3)

---

### Post by sisco311 on 2011-04-12
Thanks AlexC_ !

I stand corrected.

---

