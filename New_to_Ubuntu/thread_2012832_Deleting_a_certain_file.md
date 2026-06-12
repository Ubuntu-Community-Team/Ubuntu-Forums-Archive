---
title: "Deleting a certain file"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by Phizzurp on 2012-06-29
I made this folder to install for java. usr/local/java/. I put the wrong folder in that directory and I'm not sure how to delete it. I've tried to use the rm command but I'm obviously using it wrong. Can someone give me the right command to delete it?

---

### Post by Bucky Ball on 2012-06-29
Are you adding 'sudo' before the rm? It is:

```
sudo rmdir /your/directory/
```

Think the directory needs to be empty though else you need to add another instruction. Any reason you're not just deleting this through the file manager on the desktop?

---

### Post by Phizzurp on 2012-06-29
> **Bucky Ball said:**
> Are you adding 'sudo' before the rm? It is:

```
sudo rmdir /your/directory/
```Think the directory needs to be empty though else you need to add another instruction. Any reason you're not just deleting this through the file manager on the desktop?

It's not working. /usr/local/java/FILEHERE

That's the file I'm trying to remove. How would I?

---

### Post by Bucky Ball on 2012-06-29
What's not working? The file manager? You don't have a desktop?

If the file manager is not letting you delete, open a terminal and:

```
gksudo nautilus
```... and try again. You're in the file manager as root so ***be careful***. ;)

```
# For a directory:
sudo rmdir  /usr/local/java/DIRECTORYHERE

# For a file:
sudo rm  /usr/local/java/FILEHERE
```

---

### Post by codemaniac on 2012-06-29
```
sudo rm -rf /usr/local/java/
```

will remove everything under the java directory .

PS : **rmdir **- remove empty directories .

---

### Post by guilleme on 2012-06-30
A simple way to do it is using "rm" with some options:
```
sudo rm -rf -R /usr/local/java/THING_TO_ERASE_HERE 
```
That should do the trick. 
"rm" you know what it is. "-rf" stands for "remove forcedly", it will remove things even if they complain. "-R" is for "recursive": if you are removing a directory, it will remove all the things inside that directory as well; if you are removing a single file, well, you don`t really need it. 
Hope this helps!

---

