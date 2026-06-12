---
title: "NetBeans"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by Old-un on 2012-07-09
Decided to try out netbeans ide.  So i downloaded the software from the official netbeans site and found a file called netbeans-7.1.2-ml-php-linux.sh in my Downloads folder.

Would anyone tell me how i might install netbeans please.

---

### Post by chamber on 2012-07-09
Open a terminal, 

```
cd ~/Downloads
chmod +x netbeans-7.1.2-ml-php-linux.sh
```

This makes the file executable.  

Double click to run it.

---

### Post by Cheesemill on 2012-07-09
Why are you downloading software from websites?

Just use the Software Center to install NetBeans.

---

### Post by Superpelican12 on 2012-07-09
I would like to further explain the answer of Chamber (of course he did a good job answering Old-un's question, but I think it is a better idea to explain what someone is letting the computer do, when you let someone run some commands, especially in the case of changing permissions). For example users shouldn't change the permissions of a file too easy (that wouldn't be safe). Only when it's really necessary. Old-un probably has no idea what "chmod +x" means. I think that if you let someone change the permissions of a file, has to no what he is doing exactly. Correct me if I'm wrong. *No offence* ;) Just trying to help and give my opinion.

Anyway now I'm going to explain to Old-un what "chmod +x" means.
Chmod is an Unix command (Linux is part of the Unix-like family, it's not officialy endorsed as an Unix variant)which is used to change the permissions of files. You can add and remove permissions from a file. You have different kinds of permissions, for example the permission to read the file (r), the permission to edit the file (write, w) and the permission to execute the file (x)(if it is possible to execute it, it must be an computer program(a binary or script))(don't know if there are anymore permissions, but these are the most common I think). So called shell commands always have parameters in this case whether to add or remove a specified permission. So when you run chmod +x with the file as an additional parameter, for example:
```
chmod +x /home/your_account_name/Documents/myshellscript.sh
```
,you add the permission the execute the file to the file. You can also delete/remove a permission (for example:
```
chmod -x /home/your_account_name/Downloads/my_python_script.py
```

for more information or another (possibly better ;) )explanation visit Wikipedia(```
http://en.wikipedia.org/wiki/Chmod
```

And @Cheesemill it is possible that Old-un downloaded Netbeans from their website because he wanted the latest version (I done that to I while ago, because the repo's where still at 6.7 or 6.5, while Netbeans 7 was already available)

---

