---
title: "Using gedit - all files are duplicated and appended with ~"
date: 2007-06-16
forum: Programming Talk
---

### Post by itsalmostreal on 2007-06-16
i used to be a mac user, but i recently switched to ubuntu for the sake of staying free, and having a powerful computer that i can build and maintain on my own. currently, i use gedit for all my php editing, and i've noticed one issue: when i save a file (ie the_file.php) there is always a copy made that has a '~' added to the end of the filename (the_file.php~). 

now im not sure if this is something that happens with other apps too, but its a serious security flaw for me. anyone can add the '~' to the end of a url on my apps, and see the complete code. is there any way to disable this? while i've created a script to remove all these files before i upload, i'd much rather just not have the file appear at all.

any thoughts? thanks for any input...

---

### Post by aidanr on 2007-06-16
they are backups, you can turn it off in gedits preferences

---

### Post by aks44 on 2007-06-16
This is called a "backup" in case you didn't know... ;)

I'd say : better let gedit make backup copies, and delete them before uploading.

As a side note : being able to see the code should not be considered a security flaw. Only flawed software needs to obfuscate it's code...

---

### Post by itsalmostreal on 2007-06-16
ah ha! thanks for the speedy input...

didn't think it'd be that simple. although now im not sure i should turn it off. guess i'll have to play around and see what happens.

---

### Post by kknd on 2007-06-16
I agree with you.

The backup thing annoys me too, but I know that one day I will need it =)

---

### Post by egon spengler on 2007-06-18
> **aks44 said:**
>  As a side note : being able to see the code should not be considered a security flaw. Only flawed software needs to obfuscate it's code...

Except that he/she said this is code used for a web app, you seriously can't see ANY potential security holes from someone reading the code of a web app?

---

