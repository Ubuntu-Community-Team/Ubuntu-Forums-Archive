---
title: "&quot;sagi&quot; instead of &quot;sudo apt-get install&quot;"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Sarah L on 2008-08-30
Hi guys,

I've grown tired of typing in "sudo apt-get install" every time I wanted to install a program, so I made a little script called "sagi" that has one line:

```
sudo apt-get install $*
```

This is really fun and convenient, but my question is: is there any security risk inherent in doing this through a script? I've made my home directory part of my path and I run this script directly through there.

Thanks,
Sarah

---

### Post by Nepherte on 2008-08-30
It still requires a password for the installation, so it's not insecure.

---

### Post by gmxgeek on 2008-08-30
yeah, should be fine, all it does is save keystrokes for the user, functionality is the same

---

### Post by Bachstelze on 2008-08-30
Why make a script?

```
alias sagi="sudo apt-get install"
```

---

### Post by Vivaldi Gloria on 2008-08-30
and you can put the alias line in .bashrc in your home folder.

---

### Post by Joeb454 on 2008-08-30
> **HymnToLife said:**
> Why make a script?

```
alias sagi="sudo apt-get install"
```

I have ```
alias canhas='sudo apt-get install'
alias donotwant='sudo apt-get purge'
``` ;)

> **Vivaldi Gloria said:**
> and you can put the alias line in .bashrc in your home folder.

Or you can tell the .bashrc to look at .bash_aliases

---

### Post by mrsteveman1 on 2008-08-30
> **Joeb454 said:**
> I have ```
alias canhas='sudo apt-get install'
alias donotwant='sudo apt-get purge'
``` ;)

That's just...awesome. 

Also, if one wasn't concerned about security for some reason, you could set the script the OP has to setuid root and it won't even ask for a password :D

---

