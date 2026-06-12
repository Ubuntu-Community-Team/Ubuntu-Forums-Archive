---
title: "How to change permisions of a directory and also a file."
date: 2013-09-13
forum: New to Ubuntu
---

### Post by guillaumesoucy on 2013-09-13
Hi, 

How I can set the right to write into the file vsftpd.conf, its said I dont have the permision.I need to disable the anonymous ftp acces. 

Realy need help.

Thanks, 

Guillaume

---

### Post by Jonathan Precise on 2013-09-13
```
chmod 777 [COLOR=#000000]vsftpd.conf[/COLOR]
```

---

### Post by nerdtron on 2013-09-13
For example you have a folder which also contains files that only the "username" is able to read and write.
Folder name: sample-folder
Inside the sample-folder, there is a file: sample.cfg

You'll need to change the ownership of the folder (and file/folders inside it):
```
chown -R username:username sample-folder
```
Then make the folder (and files inside it) only readable/writeable only to the owner:
```
chmod -R 700 sample-folder
```

---

### Post by Dennis N on 2013-09-13
> **guillaumesoucy said:**
>  

I need to disable the anonymous ftp acces. 



Sounds to me like you want to edit a configuration file (belonging to root) to change some setting in it. You don't actually need to change the file's permissions for this. Instead, use elevated privileges with your text editor. This will give you temporarily the permissions to save your changes. 

That means using sudo or gksu (depending on the type of editor) when starting your editor.

example for terminal based editor nano:

**sudo nano vsftpd.conf** (assumes your working directory contains the file)

Suggest you back up the file first just in case.

---

