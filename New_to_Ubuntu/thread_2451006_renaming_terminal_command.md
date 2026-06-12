---
title: "renaming terminal command"
date: 2020-09-24
forum: New to Ubuntu
---

### Post by aidas2 on 2020-09-24
Hi

Where could i possible find a list of commands of a terminal? I want to rename one function. 
clear -> cls, as i'm still used to typing windows command CLS to clear the terminal.
Or is there an actual function to rename a function?

---

### Post by scorp123 on 2020-09-24
> **aidas2 said:**
> I want to rename one function. 
clear -> cls 

You could set an **alias **in your ~/.bashrc configuration file.  If you check your home directory there should be a file called ".bashrc".
Inside that file you could do a line that says e.g.
```

alias cls='clear'

```

Close your terminal and open it again (or start a new session) and it should be active, the command should be working.

---

### Post by TheFu on 2020-09-24
Use an alias. Don't rename programs unless you want to break your system. Badly.

Or perhaps you should rename all the programs you want. Then this learning will be first hand and have greater impact.  Most shell programs are in /bin/ or /usr/bin/  Go crazy.

But really, you should use an alias.

---

### Post by aidas2 on 2020-09-24
> **TheFu said:**
> Use an alias. Don't rename programs unless you want to break your system. Badly.

Or perhaps you should rename all the programs you want. Then this learning will be first hand and have greater impact.  Most shell programs are in /bin/ or /usr/bin/  Go crazy.

But really, you should use an alias.

You are absolutely right. Could do lots of damage I guess.

---

### Post by aidas2 on 2020-09-24
> **scorp123 said:**
> You could set an **alias **in your ~/.bashrc configuration file.  If you check your home directory there should be a file called ".bashrc".
Inside that file you could do a line that says e.g.
```

alias cls='clear'

```

Close your terminal and open it again (or start a new session) and it should be active, the command should be working.

Worked perfectly! Thanks

---

### Post by Impavidus on 2020-09-25
> **scorp123 said:**
> 
Close your terminal and open it again (or start a new session) and it should be active, the command should be working.

No need to open a new terminal or start a new session; simply sourcing your .bashrc is enough:```
. .bashrc
```

---

