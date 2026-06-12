---
title: "[Bash] cat and tar in a pipe"
date: 2012-07-13
forum: Programming Talk
---

### Post by boukli on 2012-07-13
Hi,

I just succeeded writing a little script to do backups. To compress my folders and files, I used tar and split in the following way : ```
tar -czvf - T $FILELIST | split -db 50m - $BACKUP
```The idea was to avoid using two steps, in order to save disk space.

Now, I want to concatenate and decompress the archive in a single time. I tried to use ```
cat "$BACKUP.*" > - | tar -zxvf - $DIRECTORY
``` but it doesn't work. 

Where am I wrong ? (I admit I'm a bit disappointed :confused:)

---

### Post by Bachstelze on 2012-07-13
cat already writes to standard output, you don't need > - (and anyway, it doesn't do what you think it does). Also, I'm not sure you can use * between quotes...

---

### Post by Paddy Landau on 2012-07-13
Bachstelze is correct. You should quote the $BACKUP in the first command. For the second, try:

```
cat "${BACKUP}".* | tar -zxvf - "${DIRECTORY}"
```

I am not at my computer, so I cannot test this.

I would be tempted to find the opposite of split and use that instead of cat.

---

### Post by boukli on 2012-07-14
Thank you both for your answers !

*In fine*, I removed the ```
> -
``` part, did sth different with the variable, and it works ! :P

---

