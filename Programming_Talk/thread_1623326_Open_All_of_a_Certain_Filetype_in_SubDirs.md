---
title: "Open All of a Certain Filetype in SubDirs"
date: 2010-11-16
forum: Programming Talk
---

### Post by cdusseau on 2010-11-16
I'm trying to write a script to open all of certain filetype (.ini) located in the current dir and its subdirs. So far I have had no luck, I thought this would be relatively simple, but so far I can only get it to open one file at a time with find since every time I open the file (with scite or gedit) it ties up the script until the editor is closed, at that point it will open the next file.

Any ideas that could make this easier?

---

### Post by sisco311 on 2010-11-16
```
find ./ -type f -iname "*.ini" -exec gedit '{}' +
```
See:
```
man find | less +/"-exec command \{\} \+"
```

---

### Post by IkeFalson on 2010-11-16
I'm not sure if it works in a script but $ gedit *.inp & seems to open up all the .inp files in a directory for me just fine?
I don't know how this works in a script though...
Ike

---

### Post by sisco311 on 2010-11-16
*.ini only matches the files from the current directory. The OP wants to open the files from the subdirectories as well.

In bash, if the globstar option is enabled one could use **/ to match zero or more subdirectories. 
See:
```
man bash | less +/globstar
```

```
shopt -s globstar
gedit **/*.ini
```

---

### Post by cdusseau on 2010-11-16
> **sisco311 said:**
> ```
find ./ -type f -iname "*.ini" -exec gedit '{}' +
```
See:
```
man find | less +/"-exec command \{\} \+"
```

worked perfectly, thanks...my tries were similar, just missing a couple things...

---

