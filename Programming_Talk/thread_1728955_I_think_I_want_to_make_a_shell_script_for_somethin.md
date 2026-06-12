---
title: "I think I want to make a shell script for something (specific)"
date: 2011-04-14
forum: Programming Talk
---

### Post by ClientAlive on 2011-04-14
Hi,

I'm pretty new to Linux and have been following a book to help me learn the command line. Recently I read about two commands:

```
 cp 
```

and

```
 cp -i 
```

I don't understand why anyone would want to use just "cp" since you could accidentally do something you would regret.

I was thinking it would be good to make a shell script that makes "cp" equal to "cp -i" so that if I ever forgot to include the "-i" it would save my but.

If this line of thinking seems wrong to you please tell me its wrong and I'll forget it. I don't have as much experience as you do; and, just because something seems good to me doesn't mean it is.

Otherwise I was hoping to get the code to make the shell script.

Also: there might be other things like this that I don't know about but would really save my but if I forgot to modify the command. But not if its way too much stuff please. I can understand simple things now like "cp" and "mkdir" and "rmdir", etc but some things would be way over my head.

Thanks
Jake

---

### Post by Vaphell on 2011-04-14
open .bashrc
you can find aliases there
simply add your own

aliases work like simple substitution
for example
alias grep='grep --color=auto'
you type grep <something>, then grep is replaced with the value of alias (grep --color=auto) and then executed (grep --color=auto <something>)

aliases are great for simple stuff, if your custom 'device' needs to be smarter than that then you need scripts

---

### Post by ClientAlive on 2011-04-14
Ok. Thaks.

---

