---
title: "Can't count specific files"
date: 2011-08-01
forum: Programming Talk
---

### Post by slashwannabe94 on 2011-08-01
I was wondering how i would count **only** the files in the current directory and ignore all directories with and without the .. or . prefix. I have got as far as this, but i still end up counting the directories.
ls -a -l | grep -v ^l | wc -l

It's frustrating because i know that i can count all the directories and ignore files, but i can't do it the other way around. 
ls -a -I .. -1 --file-type --group-directories-first | grep / | wc -l

Thanks people,  
SlashWannabe94

---

### Post by Bachstelze on 2011-08-01
```
find . -maxdepth 1 -type f | wc -l
```

---

### Post by sisco311 on 2011-08-01
Eh, your command will fail if the directory contains a file with a newline in its name. Check out: [http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004)

You can use find to list the files. Read the output of find in a array and print the length of the array. 

Didn't tested it, but try something like:
```

files=()
while IFS= read -d '' -r file
do
    files+=("$file")
done< <(find ./ -maxdepth 1 -type f -print0)
echo "${#files[@]}"

```

---

### Post by slashwannabe94 on 2011-08-01
> **Bachstelze said:**
> ```
find . -maxdepth 1 -type f | wc -l
```
Awesome, that's exactly what i was looking for. Thanks so much Bachstelze

SlashWannabe94

---

### Post by slashwannabe94 on 2011-08-01
> **sisco311 said:**
> Eh, your command will fail if the directory contains a file with a newline in its name. Check out: [http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004)

You can use find to list the files. Read the output of find in a array and print the length of the array. 

Didn't tested it, but try something like:
```

files=()
while IFS= read -d '' -r file
do
    files+=("$file")
done< <(find ./ -maxdepth 1 -type f -print0)
echo "${#files[@]}"

```

That works too :D 

Thanks, 
SlashWannabe94

---

