---
title: "can change or copy files to /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/audio"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by dmurat on 2008-09-10
as i said, i cant copy or create an item to the folder /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/audio
i need to do this for to paste a soundbank. the error message is: ```
error:  cannot create /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/audio/soundbank-deluxe.gm

```

why does such a thing happens and is there anything i can do?

---

### Post by aloshbennett on 2008-09-10
If its permission related, launch nautilus using
> gksudo nautilus

Remember: You are running nautilus as root. Be careful what you are deleting.

---

### Post by dmurat on 2008-09-10
i ran nautilus but i didnt understand what can i do with it? it directs me to the root folder and then what..?

---

### Post by aloshbennett on 2008-09-11
type in /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/audio in the adress bar. Once you are there, copy any file you wanted to here.

Btw, what exactly are you doing?

---

### Post by gvartser on 2008-09-11
As said in previous posts you need to do this as an privileged users: "root":

This is how you do it from a terminal/shell:
1) Open up a terminal/shell.
2) cd into the directory where the file is located:
   ```
cd /<path>/<to>/<source_directory>
```
3) Copy the file as root:
   ```
sudo cp soundbank-deluxe.gm /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/audio/
```
4) Done!

/g

---

