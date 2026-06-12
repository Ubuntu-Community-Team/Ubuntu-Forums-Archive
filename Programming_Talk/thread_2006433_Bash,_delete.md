---
title: "Bash, delete"
date: 2012-06-19
forum: Programming Talk
---

### Post by prismctg on 2012-06-19
How to remove all content from  "example" folder , but i dont want to remove the "example" folder

---

### Post by click4851 on 2012-06-19
couldn't you use some wild cards to indicate all files and then provide the location of the folder? (just have to be careful with wildcards)

Something like this...

[http://forums.techarena.in/windows-software/1373668.htm](http://forums.techarena.in/windows-software/1373668.htm)

---

### Post by nothingspecial on 2012-06-19
```
rm -r example_folder/*
```
[URL="http://mywiki.wooledge.org/BashGuide/Patterns"][COLOR="RoyalBlue"]
Patterns[/COLOR][/URL]

---

### Post by prismctg on 2012-06-19
Thanx all of you guys  :)

---

### Post by v8YKxgHe on 2012-06-19
> **nothingspecial said:**
> ```
rm -r example_folder/*
```
[URL="http://mywiki.wooledge.org/BashGuide/Patterns"][COLOR="RoyalBlue"]
Patterns[/COLOR][/URL]

Be careful when using this, as it doesn't do *exactly* what you may want it to do. For example, in Bash the wildcard glob "*" does not match dot-files by default, and you need to enable the "dotglob" option.

The following will suffice:

```
shopt -s dotglob
rm -r example_folder/*
```

---

### Post by prismctg on 2012-06-19
> **AlexC_ said:**
> Be careful when using this, as it doesn't do *exactly* what you may want it to do. For example, in Bash the wildcard glob "*" does not match dot-files by default, and you need to enable the "dotglob" option.

The following will suffice:

```
shopt -s dotglob
rm -r example_folder/*
``` thank you AlexC

---

