---
title: "[SOLVED] Simple bash question"
date: 2008-06-01
forum: Programming Talk
---

### Post by schauerlich on 2008-06-01
I want to create a set of directories which repeats recursively within itself. For example, it would make /a, /b, /c, and then /a/a, /a/b, /a/c, /b/a, /b/b, /b/c, /c/a, /c/b, /c/c and so on. Is there a simple way of doing this?

---

### Post by original_jamingrit on 2008-06-01
Like this?

```

mkdir testing_directory
cd testing_directory

DIR_NAMES=( a b c )

for i in ${DIR_NAMES[@]}; do for j in ${DIR_NAMES[@]}; do mkdir -p "$i/$j"; done; done;


```

That last line can be broken down into
```
for i in ${DIR_NAMES[@]}; do 
  for j in ${DIR_NAMES[@]}; do 
    mkdir -p "$i/$j";
  done;
done;
```

the command 'mkdir -p foo/foo' creates parent directories when necessary.

---

### Post by schauerlich on 2008-06-01
Thanks, that worked just fine.

---

### Post by GrouchoMarx on 2008-06-01
If you wanted the pattern to continue to arbitrary depth then you could modify like so:

```
#! /bin/bash

DEPTH=0
MAX_DEPTH=3
DIR_NAMES=( a b c )

function dir-recurse () {
    cd $1
    ((DEPTH++))
    for dir in ${DIR_NAMES[@]}; do
        mkdir $dir
        if [ $DEPTH -lt $MAX_DEPTH ]; then dir-recurse $dir; fi
    done
    cd ..
    ((DEPTH--))
}

mkdir test
dir-recurse test


```

---

