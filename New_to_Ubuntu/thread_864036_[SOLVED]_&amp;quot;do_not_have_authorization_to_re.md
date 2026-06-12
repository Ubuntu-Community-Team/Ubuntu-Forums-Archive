---
title: "[SOLVED] &amp;quot;do not have authorization to read file&amp;quot; ?help?"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by steve joe bob on 2008-07-19
so i have an ipod that was formated to be used with a mac computer. i basically use it as a giant flash drive. i have a bunch of files that i would like to get off of it. i don't have access to a mac computer at the moment. so i plugged it into my dual boot xp/ubuntu machine. obviously xp has no clue that there is nething on or that it's even usable without wanting to reformat it. ubuntu on the other hand saw it and i was able to open it and view all the files. it just said i don't have have authorization to view the or read them or whatever the exact error was. anyways how do i go about getting authorization? i would like to pull them off the ipod so i can use them :P. i'm the only user on the computer so i dont understand why i wouldn't have authorization. any help would be much appreciated. thnx in advance :)

---

### Post by iaculallad on 2008-07-19
> **steve joe bob said:**
> so i have an ipod that was formated to be used with a mac computer. i basically use it as a giant flash drive. i have a bunch of files that i would like to get off of it. i don't have access to a mac computer at the moment. so i plugged it into my dual boot xp/ubuntu machine. obviously xp has no clue that there is nething on or that it's even usable without wanting to reformat it. ubuntu on the other hand saw it and i was able to open it and view all the files. it just said i don't have have authorization to view the or read them or whatever the exact error was. anyways how do i go about getting authorization? i would like to pull them off the ipod so i can use them :P. i'm the only user on the computer so i dont understand why i wouldn't have authorization. any help would be much appreciated. thnx in advance :)

Try to launch privilege nautilus and browse the folder location of the file to view/read:

```
gksudo nautilus
```

---

