---
title: "meaning of &quot;\&quot; in &quot;\mkdir ...&quot;"
date: 2009-02-26
forum: Programming Talk
---

### Post by flylehe on 2009-02-26
Hi,
In a bash shell script, what does "\" mean in "\mkdir ...". or more generally in "\command"? "\" here seems not treating the following charaters literally, but instead executes the command. So what does it make a difference than not using "\"? Thanks!

---

### Post by snova on 2009-02-26
Doesn't expand aliases. For example, in an uncustomized Bash session:

```

$ alias ll='ls -l'
$ ll
# Works as expected ...
$ \ll
bash: ll: command not found

```

---

### Post by flylehe on 2009-02-26
Thank you! 

So in my case, mkdir could have been defined as alias of other command? And using "\mkdir" will ensure the bash command mkdir will be executed? 

I searched the whole script, no mkdir appeared before the use of "\mkdir" and "\mkdir" is its only appearance. So what could the purpose of "\mkdir" possibly be?

Thanks!

---

### Post by simeon87 on 2009-02-26
> **flylehe said:**
> Thank you! 

So in my case, mkdir could have been defined as alias of other command? And using "\mkdir" will ensure the bash command mkdir will be executed? 

I searched the whole script, no mkdir appeared before the use of "\mkdir" and "\mkdir" is its only appearance. So what could the purpose of "\mkdir" possibly be?

Thanks!

I think you answered your own question.. it prevents an alias mkdir instead of the command mkdir to be executed.

---

