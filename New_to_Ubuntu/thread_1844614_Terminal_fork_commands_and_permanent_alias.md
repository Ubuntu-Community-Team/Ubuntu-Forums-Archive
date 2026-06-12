---
title: "Terminal: fork commands and permanent alias?"
date: 2011-09-15
forum: New to Ubuntu
---

### Post by Zephilinox on 2011-09-15
Don't really know what to call it, but for example if I wanted to install two packages, I would normally have to do this

```
sudo apt-get install alpha1 && sudo apt-get install alpha2
```

Is there any way I can do it like this? (but you know, with it actually working)

```
sudo apt-get install alpha1 && alpha2
```

it would save a lot of typing time, and I remember there being a file I had to add alias commands to in order for them to be stored across terminals/boots but I can't remember the name, any one know?

---

### Post by nothingspecial on 2011-09-15
```
sudo apt-get install alpha1 alpha2
```

Put an alias in your .bashrc eg

```
alias inst='sudo apt-get install'
```

source bash

```
. ~/.bashrc
```

Now it's ```
inst alpha1
```

:D

EDIT except as sisco is about to point out any minute now, aliases don't take more than one argument. So use a function instead, if you want to install more than one package.

---

### Post by sisco311 on 2011-09-15
```
sudo apt-get install alpha1 alpha2
```

The file you are looking for is: ~/.bashrc

Instead of aliases, I'd use functions, see:
[http://mywiki.wooledge.org/BashFAQ/080](http://mywiki.wooledge.org/BashFAQ/080)
[http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions)

*Aliases don't work in scripts, they can't take arguments and they have special evil magical powers that break all expectations*. :)

---

### Post by Zephilinox on 2011-09-15
Thanks you two, very quick responses :) thread solved.

---

### Post by ibutho on 2011-09-15
Aliases can be saved in ~/.bashrc for an individual and globally in /etc/bash.bashrc.

---

