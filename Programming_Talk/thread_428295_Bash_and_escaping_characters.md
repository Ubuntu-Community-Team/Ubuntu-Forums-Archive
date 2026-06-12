---
title: "Bash and escaping characters"
date: 2007-04-30
forum: Programming Talk
---

### Post by coolix on 2007-04-30
Ok let's put it simply:

```
$ ls -l
total 8
drwxr-xr-x 2 coolix coolix 4096 2007-04-30 12:00 another_dir
drwxr-xr-x 2 coolix coolix 4096 2007-04-30 11:58 dir containing spaces

```

I have two dirs, one containing spaces in name

```

$ find ~/test -mindepth 1 -maxdepth 1
/home/coolix/test/dir containing spaces
/home/coolix/test/another_dir
```

Let's say that i want to use the output of the first find to a second one :

```
$ find `find ~/test -mindepth 1 -maxdepth 1`
find: /home/coolix/test/dir: No such file or directory
find: containing: No such file or directory
find: spaces: No such file or directory
/home/coolix/test/another_dir
```

Spaces should be escaped (i think) and i havent found a valid method to do it yet

Here's what i tried so far :

```
$ find ~/test -mindepth 1 -maxdepth 1 | sed 's/ /\\ /g'
/home/coolix/test/dir\ containing\ spaces
/home/coolix/test/another_dir

$ find `find ~/test -mindepth 1 -maxdepth 1 | sed 's/ /\\ /g'`
find: /home/coolix/test/dir: Aucun fichier ou répertoire de ce type
find: containing: Aucun fichier ou répertoire de ce type
find: spaces: Aucun fichier ou répertoire de ce type
/home/coolix/test/another_dir
```

I'm lost, any help would be greatly appreciated !

---

### Post by cwaldbieser on 2007-04-30
> **coolix said:**
> Ok let's put it simply:

```
$ ls -l
total 8
drwxr-xr-x 2 coolix coolix 4096 2007-04-30 12:00 another_dir
drwxr-xr-x 2 coolix coolix 4096 2007-04-30 11:58 dir containing spaces

```

I have two dirs, one containing spaces in name

```

$ find ~/test -mindepth 1 -maxdepth 1
/home/coolix/test/dir containing spaces
/home/coolix/test/another_dir
```

Let's say that i want to use the output of the first find to a second one :

```
$ find `find ~/test -mindepth 1 -maxdepth 1`
find: /home/coolix/test/dir: No such file or directory
find: containing: No such file or directory
find: spaces: No such file or directory
/home/coolix/test/another_dir
```

Spaces should be escaped (i think) and i havent found a valid method to do it yet

Here's what i tried so far :

```
$ find ~/test -mindepth 1 -maxdepth 1 | sed 's/ /\\ /g'
/home/coolix/test/dir\ containing\ spaces
/home/coolix/test/another_dir

$ find `find ~/test -mindepth 1 -maxdepth 1 | sed 's/ /\\ /g'`
find: /home/coolix/test/dir: Aucun fichier ou répertoire de ce type
find: containing: Aucun fichier ou répertoire de ce type
find: spaces: Aucun fichier ou répertoire de ce type
/home/coolix/test/another_dir
```

I'm lost, any help would be greatly appreciated !

I am not sure why you would want to do this:
```

$ find ~/test -mindepth 1 -maxdepth 1 -print0 | xargs --null find

```
Maybe if you elaborated a little on what you are trying to accomplish.

---

### Post by lloyd_b on 2007-04-30
Instead of trying to escape the spaces, try wrapping the file names in double quotes instead:
```
find ~/test -mindepth 1 -maxdepth 1 -printf '"%p"\n'
```
and see if this solves the issue.

Lloyd B.

---

