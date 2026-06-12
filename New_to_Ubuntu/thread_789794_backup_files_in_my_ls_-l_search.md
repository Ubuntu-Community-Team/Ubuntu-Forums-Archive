---
title: "backup files in my ls -l search"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by williamburn on 2008-05-10
I was wondering if anyone could tell me why, when i search:

$ls -l

the results will contain :
test.txt
test.txt~

The ~ after the file denotes a backup

I can search using the $ls -lB , but that is a pain in the you know what. I am still fairly new to linux.  First of all can you tell me why it does this behavior and secondly how to disable it?

Thank you in advance.

---

### Post by Joeb454 on 2008-05-10
It's the settings in some applications :) You'll have to look at the settings for the application you write the files with.

---

### Post by llamakc on 2008-05-10
Why would you want to disable it? I have found the auto-backup function for text editors to be invaluable.

---

### Post by Rocket2DMn on 2008-05-10
You can make an alias of the ls command in your .bashrc file to always include the -B options when you use the ls command.
```
gedit ~/.bashrc
```
Somewhere in the file add then line
```
alias ls='ls -B'
```
Save and close, then either restart terminal or just this once run
```
source ~/.bashrc
``` 
Now when you run the ls command that -B option is automatically used.

---

### Post by williamburn on 2008-05-10
Gedit had the setting that said keep a backup copy.  That was driving me bananas.  When i searched it was keeping a huge list of files.  I am doing some programming lessons, and frankly its annoying to me.  Thank you so much for the quick reply.

---

### Post by unutbu on 2008-05-10
If you edit your .bashrc file, by adding the line
```
alias ll='ls -lB'
```
then you can type ll at any terminal prompt and get the same result as ls -lB.

---

### Post by Joeb454 on 2008-05-10
Usually when I'm done working I'll use the terminal to go to the directory I was working in (say it was /home/joe/programming (a.k.a ~/programming)) and execute a nice simple command to get rid of them all :)

```
rm -f *.*~
```

Basically what this does is delete any file, with any extension, that has a '~' at the end of it :)

---

