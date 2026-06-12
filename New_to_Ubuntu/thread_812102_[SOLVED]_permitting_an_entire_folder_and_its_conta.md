---
title: "[SOLVED] permitting an entire folder and its containments"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-05-29
I would like to allow permissions for an entire folder including all of its sub folders and files etc.

I know ```
sudo chmod 777 filename
``` allows individual folders/files to be permitted, but it isn't convenient for a folder that is filled with files and sub folders that I want to be permitted access to for viewing and editing. So how can I do this?

Thanks in advance :)

---

### Post by amingv on 2008-05-29
try:
```
sudo chmod -R 777 foldername
```

---

### Post by JimmyJim on 2008-05-29
> **amingv said:**
> try:
```
sudo chmod -R 777 foldername
```

Thanks, it worked :)

---

