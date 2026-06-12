---
title: "Unable to access jarfile /home/matthew/jedit/4.2/jedit.jar"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by matt_wood87 on 2008-11-25
Hi

I used to have jedit installed on ubuntu, i uninstalled it, and then reinstalled it through synaptics package manager having made it appear there by adding to the list of sources.

now when i type "jedit" into a terminal, i get the error message
Unable to access jarfile /home/matthew/jedit/4.2/jedit.jar


i know where the new location of jedit.jar is,
"/usr/share/jedit/jedit.jar"

what do i need to edit so that i can change the location ubuntu think jedit is.

any help would be much appreciated!

thanks

Matt

---

### Post by wizard10000 on 2008-11-25
Create the directory /home/matthew/jedit/4.2

then

```
cd /home/matthew/jedit/4.2

ln -s /usr/share/jedit/jedit.jar jedit.jar
```

---

### Post by matt_wood87 on 2008-11-25
hi,
thanks for the reply, is this not a bit of a hacky workaround? creating a redundant directory and linking the file to it. Is it not possible repoint that original link that is being followed to the directory that no longer exisits, surely that must be possible?

many thanks for reply, i'll give it a go if i dont get a cleaner solution

Matt

---

### Post by wizard10000 on 2008-11-25
> **matt_wood87 said:**
> hi,
thanks for the reply, is this not a bit of a hacky workaround? creating a redundant directory and linking the file to it. Is it not possible repoint that original link that is being followed to the directory that no longer exisits, surely that must be possible?

many thanks for reply, i'll give it a go if i dont get a cleaner solution

Matt

Hi, Matt - 

I figure you're gonna hack something either way  :)

After reading jedit's man page I can't think of a way to do it that doesn't require a symlink but maybe someone else has a better idea.

edit:  I guess you could compile from source - it's Ubuntu's package that's broken, not jedit.  Apparently the package installs jedit in a nonstandard location   ;)

---

### Post by matt_wood87 on 2008-11-25
thanks! i guess i assumed it wasnt so much a problem with jedit more a problem with ubuntu and how the terminal reacts to the jedit command but i dont know how to change that.

thanks again

Matt

---

### Post by sdnelson on 2008-11-25
Try this..


java -jar jedit.jar

---

### Post by taralee324 on 2009-04-22
In case anyone else finds this thread on a Google search...

To resolve this:
1.) Type "which jedit" in the command line
2.) Edit the echoed file to refer to the correct directory.

---

