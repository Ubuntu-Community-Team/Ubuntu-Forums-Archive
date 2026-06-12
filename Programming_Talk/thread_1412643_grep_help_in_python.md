---
title: "grep help in python"
date: 2010-02-21
forum: Programming Talk
---

### Post by danastasio on 2010-02-21
Alright, I am writing a program to interface with the Arch Linux AUR for a friend. I need help with grep. So far as I can tell, the only way to actually search the thing is to download the HTML code and grep the information out of it. The problem I have is when you run

```
grep packages.php?ID=
``` 

(grepping just the package name gives stuff you dont need "packages.php?ID=" only shows up in the lines with the package names)

it returns this:

> <td class='data1'><span class='f4'><a href='packages.php?ID=20401'><span class='black'>python-yolk 0.4.1-1</span></a></span></td>

In this particular case, "Python-yolk 0.4.1" is the only thing that I am interested in. Is there any way that I can grep just that out of a file without getting the whole line?

I probably worded this poorly, so let me know if I can restate anything :)

---

### Post by DaithiF on 2010-02-21
you could pipe the results into another command to strip out the parts you don't want.
e.g. this sed command will eliminate anything within angle brackets, thus leaving you with just the package name:

```
grep something something | sed 's/<[^>]*>//g'
```

---

### Post by falconindy on 2010-02-21
The AUR has a JSON RPC interface which is lightyears faster than fetching and parsing pages. All the latest AUR helpers like bauerbill, clyde, and slurpy use the JSON interface. As slurpy is written in Python, you may want to have a look at its code to figure out how to proceed.

edit: look at [http://aur.archlinux.org/rpc.php](http://aur.archlinux.org/rpc.php) for usage.

---

