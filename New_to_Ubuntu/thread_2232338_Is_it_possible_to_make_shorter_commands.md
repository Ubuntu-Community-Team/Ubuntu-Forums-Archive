---
title: "Is it possible to make shorter commands?"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by LBnYBzr on 2014-07-01
I have a python script that I run manually fairly frequently. It takes the usage myscript.py <argument>

Instead of typing all of that, I would just like to type: a <argument>
Or even better I would simply just like to only type the argument in the shell: <argument> 

Is it possible to make an "alias" for a command in this way?

---

### Post by sudodus on 2014-07-01
Yes, ***alias*** is part of the linux tool-box

Find the part of the file **~/.bashrc** where there are already aliases, and add your own. I add these (plus around 50 other aliases)

```
alias rm='rm -i'
alias l='ls -l --group-directories-first'
```

and when I want to help someone and need to remove my locale (local language settings)

```
alias LC='LC_ALL=C;LANG=C'
```

So I use the short commands ***rm*** and ***l*** with new meanings and the new command ***LC***

---

### Post by robert107 on 2014-07-01
an alternative would be making a symbolic link with concise name in your $PATH to your Python script

---

