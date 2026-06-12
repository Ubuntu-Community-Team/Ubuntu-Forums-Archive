---
title: "Extracting hundreds of .rar at once"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by ACJarrett on 2008-05-09
Hey all,

I'm looking for a good program to extract folders from hundreds of different .rar files.

I tryed using Arc but when i tell it to extract *.rar from my desktop it opens them all and freezes.

i'm using the terminal command 
```
arc /home/[User Name]/Desktop/[Torrented Folder]/*.rar /home/[User Name]/.fretsonfire/songs
```

The code might be a little bit off cause i'm going from memory but it does run through.

Thanks in advance!

---

### Post by tjwoosta on 2008-05-09
i guess this might be a stupid question but have you tried unrar?

it should be in synaptic package manager

---

### Post by Monicker on 2008-05-09
arc may be trying to suck in more info than it can handle about the files.

I'll just modify my one liner from the other post.  :P

```
#!/bin/bash

for rarfile in /home/username/Desktop/TorrentFolder/*.rar
do
   arc "$rarfile" /home/username/.fretsonfire/songs
done
```

Save it as unarc.sh or something, do chmod +x unarc.sh to make it executable,

./unarch.sh to run.  If it works you should probably move it to /usr/local/bin


This will process each file sequentially, and should put less of a memory load on the application.  It will still take a while, depending on the number and size of the files.

---

### Post by ACJarrett on 2008-05-09
Heh, no i haven't.  I'll check it out once i get home.  Thanks for the advice tj!  :)

haha and thanks Monicker!  thats exactly what i'm looking for.  I appreciate it.

---

