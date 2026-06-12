---
title: "Could not initialize package information"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by kittykatmeowmeow on 2008-07-01
I am getting the following error message when I try to download updates through Update Manager:
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'universe' is not known on line 86 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Please help!

---

### Post by plucky on 2008-07-02
> **kittykatmeowmeow said:**
> I am getting the following error message when I try to download updates through Update Manager:
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'universe' is not known on line 86 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

Please help!


Open a terminal and post the output of ```
cat /etc/apt/sources.list
```Please place the output in **[noparse]```

```[/noparse]** BB Code brackets.

---

### Post by kittykatmeowmeow on 2008-11-09
I am still getting the error message even after I paste
 cat /etc/apt/sources.list into the terminal.

---

### Post by plucky on 2008-11-10
> **kittykatmeowmeow said:**
> I am still getting the error message even after I paste
 cat /etc/apt/sources.list into the terminal.

That command displays your **sources.list** and you need to copy and paste it into the forums so we can see it as 

> 'E:Type 'universe' is not known on line 86 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


says there is something amiss in line 86.For us to correct the problem,we have to see what the problem is.

P.S. 4 months later? Click on **BBcode list** in my signature.

---

