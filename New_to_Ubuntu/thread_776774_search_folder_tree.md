---
title: "search folder tree"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by ecs_pf5 on 2008-04-30
I'm looking for a file named something like -98y34rf98y3efy.flv

I know it's been created by a script I wrote, but where?

What tool can I use on Kubuntu, to help me find it?

To use MSDOS terminology I guess I'm wanting to look everywhere, for *.flv

[edit] python created the file, from a script I ran in a folder on my Desktop. But it's not visible in that folder, nor my home directory or Desktop, nor root, nor even /usr/bin/

---

### Post by tamoneya on 2008-04-30
```
find / -name *98y34rf98y3efy.flv
```You can use "*" as a wild card if you arent totally sure of the name.  If that doesnt work try *.flv since you seem to know the extension and you should find it as long as you dont have to many flv files on your computer.

---

### Post by Monicker on 2008-04-30
> **ecs_pf5 said:**
> I'm looking for a file named something like -98y34rf98y3efy.flv

I know it's been created by a script I wrote, but where?

What tool can I use on Kubuntu, to help me find it?

To use MSDOS terminology I guess I'm wanting to look everywhere, for *.flv


From a termial:

```
find /some/dir -name *.flv
```

That will recursively search from the start point.

---

### Post by ecs_pf5 on 2008-04-30
Good one guys thanks :)

---

