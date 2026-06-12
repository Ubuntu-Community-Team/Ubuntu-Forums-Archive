---
title: "A bash question"
date: 2009-07-28
forum: Programming Talk
---

### Post by flylehe on 2009-07-28
Hi,
I am trying to redirect my output to a file and need to first put a command into a string. Here is the error:
```

bash-3.2$ cc="(date && time ls -l -a && date) > ./tmp/log"
bash-3.2$ $cc
bash: (date: command not found

```
What's wrong? 
Thanks and regards!

---

### Post by flylehe on 2009-07-28
Hi,
I am trying to redirect my output to a file and need to first put a command into a string. Here is the error:
```

bash-3.2$ cc="(date && time ls -l -a && date) > ./tmp/log"
bash-3.2$ $cc
bash: (date: command not found

```
What's wrong? 
Thanks and regards!

---

### Post by stroyan on 2009-07-28
Using just $cc will not parse the contents of the cc variable as if it was a shell command.
The shell is trying to use the "(date" part as an executable name.
You can get the effect that you are describing using
```
eval $cc
```
to ask the shell to parse the contents of cc.

---

### Post by grizzler on 2009-07-28
When bash executes the commands in the variable cc, it uses everything 'as is', i.e. it starts with executing **(date** instead of just **date**. I don't know if there's a way around this, but I have used an alias for a similar purpose. Try this:

```
alias cc='(date && time ls -la && date) &>./tmp/log'
```

Execute with **cc** (no $).

Don't forget the ampersand immediately before the greater-than sign, or part of the time output will appear on screen instead of in your file.

---

### Post by kk0sse54 on 2009-07-28
You might want to pick something different than cc, as cc is the command for your C compiler. I don't know really how you use your system and if it will effect you but just so that you're aware ;). You can also check out 'man cc'

---

### Post by spillin_dylan on 2009-07-28
> **flylehe said:**
> Hi,
I am trying to redirect my output to a file and need to first put a command into a string. Here is the error:
```

bash-3.2$ cc="(date && time ls -l -a && date) > ./tmp/log"
bash-3.2$ $cc
bash: (date: command not found

```
What's wrong? 
Thanks and regards!

How about something more along the lines of: 
```

bash-3.2$ cc=`date && time ls -l -a && date` 
bash-3.2$ echo $cc &> ./tmp/log

```

Notice the `backquotes` which execute statements inside them, then assign it to cc.

---

### Post by Rocket2DMn on 2009-07-28
Threads merged.  Please don't create multiple threads on the same topic - it isn't fair to those volunteering their time here, and doesn't result in getting more or better help.
Thank you.

---

