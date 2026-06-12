---
title: "copy two files to every subfolder in a folder"
date: 2018-11-25
forum: Programming Talk
---

### Post by cazz on 2018-11-25
Hi
I trying to make a nice gallery for my image
In every image folder I going to have one PHP file and one text file (index.php, page.txt) and the page.txt file have to have 666 because it going to be some writing inside it.

The folder structure is build like this

```
My start folder
|-lib
   |-Area 1
       |-Subject 1
       |-Subject 2
   |-Area 2
       |-Subject 1
       |-Subject 2
….
```


is in the subject folder (The all have diffrent names then subject) I like to have a copy of the php and textfile

if that is a php and text file in the folder just let it be.


So I going to run this code everyting I have upload a new gallery but right now I have alot of folder that need the php and text file is that any easy way for me to make a script that copy the files??

---

### Post by TheFu on 2018-11-25
Keep the php files and data separate.  Basic security architecture.
The design as laid out is a good way to be hacked.  Having writable directories where PHP code sits is a terrible idea.
[https://secure.php.net/manual/en/security.php](https://secure.php.net/manual/en/security.php)

If a web process can create a file to the same directory, then they can replace the php code there too.

---

### Post by cazz on 2018-11-25
yes but this is on a local webserver only access in my own network.
the text file only have a number inside and that all and I only want the text file to be 666

---

