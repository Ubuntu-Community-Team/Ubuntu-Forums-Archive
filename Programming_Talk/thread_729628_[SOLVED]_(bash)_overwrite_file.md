---
title: "[SOLVED] (bash) overwrite file"
date: 2008-03-20
forum: Programming Talk
---

### Post by Balazs_noob on 2008-03-20
Hi guys
i would haves small problem with bash...
my task would be to locate a chat.txt file(there is only one)
in my home folder and change all joseph to joe and all
marry to zoe.

i made this:
```

find ./home/balazs -name "chat.txt" | xargs sed 's:joseph:joe:g' |sed 's:marry:zoe:g'>`find ./home/balazs -name "chat.txt"`

```it works great when i write the result to the standard output
but it makes a blank file when try to redirect it back
into the original file

any help would be appreciated :)

Balázs

---

### Post by croto on 2008-03-20
hey, I guess the problem is that you are writing to the same file you're processing, so it gets overwritten at the beginning and then there's nothing to process. So just write the result to a temporary file, and then rename it to the name you want to give it.

---

### Post by bashologist on 2008-03-20
This might work like you want. I'm pretty sure.

```
find ~balazs -name 'chat.txt' -exec sed -i.bak 's/joseph/joe/g; s/marry/zoe/g' {} \;

```

---

### Post by Balazs_noob on 2008-03-20
thank you it worked great :D

i am just reading the man pages to find out how it works ;)

Thread solved

---

