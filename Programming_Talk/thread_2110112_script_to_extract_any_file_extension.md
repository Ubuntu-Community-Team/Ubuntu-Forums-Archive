---
title: "script to extract any file extension"
date: 2013-01-29
forum: Programming Talk
---

### Post by IAMTubby on 2013-01-29
Hey,
I remember seeing here a script to extract any file extension. I tried searching using all related keywords like {extract, extension, unzip etc), but I just can't find it :(

Does anyone have it ?

Thanks.

---

### Post by r-senior on 2013-01-29
Do you mean extract files from some sort of an archive or extract a file extension from a filename?

What is it you are trying to do?

---

### Post by IAMTubby on 2013-01-29
> **r-senior said:**
> Do you mean extract files from some sort of an archive or extract a file extension from a filename?
What is it you are trying to do?
Hello r-senior,
to extract files from an archive, like unzip <name>.zip

---

### Post by Cheesemill on 2013-01-29
Add the following extract function to your ~/.bashrc file...
```
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}
```You can then use 'extract <filename>' to automatically extract an archive with the correct program.


There are various versions of this floating around the interweb, doing a search for '.bashrc extract function' should find them all.

---

### Post by Vaphell on 2013-01-29
i'd add double quotes around $1 because currently that code assumes no-whitespace names.

---

### Post by IAMTubby on 2013-01-30
> **Cheesemill said:**
> Add the following extract function to your ~/.bashrc file...
```
extract () {
     if [ -f $1 ] ; then
         case $1 in
             *.tar.bz2)   tar xjf $1        ;;
             *.tar.gz)    tar xzf $1     ;;
             *.bz2)       bunzip2 $1       ;;
             *.rar)       rar x $1     ;;
             *.gz)        gunzip $1     ;;
             *.tar)       tar xf $1        ;;
             *.tbz2)      tar xjf $1      ;;
             *.tgz)       tar xzf $1       ;;
             *.zip)       unzip $1     ;;
             *.Z)         uncompress $1  ;;
             *.7z)        7z x $1    ;;
             *)           echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}
```You can then use 'extract <filename>' to automatically extract an archive with the correct program.


There are various versions of this floating around the interweb, doing a search for '.bashrc extract function' should find them all.
Cheesemill, wow :D
exactly what I needed. thanks a lot.

---

### Post by IAMTubby on 2013-01-30
> **Vaphell said:**
> i'd add double quotes around $1 because currently that code assumes no-whitespace names.
Vaphell, around each one of them from Cheesemill's script?

---

### Post by Vaphell on 2013-01-30
in *if* condition and for each command

---

