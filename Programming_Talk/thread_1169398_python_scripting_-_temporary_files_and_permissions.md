---
title: "python scripting - temporary files and permissions"
date: 2009-05-25
forum: Programming Talk
---

### Post by GOwin on 2009-05-25
I have a script that generates a temporary file, which is supposed to be processed and deleted by another program. 
```


import os, tempfile

f = tempfile.NamedTemporaryFile(dir='/var/outgoing', delete=False)
f.write("46562\nWhat are you doing, stranger?")
f.flush()
f.close

```

However, the other program complains that it cannot process the file and I found the files being generated with permissions like:

```

-rw-------  1 jack jack           42 2009-05-25 16:32 tmp3Wawb9

```


This is the permission settings of the folder:
```

drwxrwsr-t 2 proggie proggie 4096 2009-05-25 16:12 outgoing

```

I already tried making myself a member of the proggie group but the python script I got cannot write to the outgoing directory. And the only way I got it to write to the folder is to run
```
chmod a+rw /var/outgoing
```

What I want to do is generate a temporary file in that folder, which will be deleted later by another process outside my script.

I know I'm doing something wrong here but I can't figure it out.

---

### Post by GOwin on 2009-05-25
geesh. I knew it was a dumb question.
```

umask

```

---

### Post by GOwin on 2009-05-25
Unfortunately, I don't like the consequences of setting the umask.

Is there a way to set a umask just for a specific directory? What's the best way to resolve this issue?

---

### Post by unutbu on 2009-05-25
How about use 
```
from stat import S_IRUSR,S_IWUSR,S_IRGRP,S_IWGRP,S_IROTH,S_IWOTH

os.chmod(f.name,S_IRUSR|S_IWUSR|S_IRGRP|S_IWGRP|S_IROTH|S_IWOTH)
```

to manually alter the permissions for just the one file? The above gives read/write permissions to user, group and other.

---

### Post by imdano on 2009-05-25
> **unutbu said:**
> How about use 
```
from stat import S_IRUSR,S_IWUSR,S_IRGRP,S_IWGRP,S_IROTH,S_IWOTH

os.chmod(f.name,S_IRUSR|S_IWUSR|S_IRGRP|S_IWGRP|S_IROTH|S_IWOTH)
```

to manually alter the permissions for just the one file? The above gives read/write permissions to user, group and other.
You could also just do
```
os.chmod(f.name, 0666)
```

---

### Post by unutbu on 2009-05-25
Oh... LOL!

Thanks, imdano :)

---

### Post by GOwin on 2009-05-26
what i did was to run the sudo the script with the username of the other process.

Thanks for this tip. It's noted.

---

