---
title: "[SOLVED] opt directory"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by waterrr on 2008-08-04
hi all,
ive copied some files into the opt directory, but only as the root from using ```
gksu nautilus
``` and when i try to write commands in that directory from a diff. user, lets say user123, im not able to - how can i fix this?

---

### Post by acidsolution on 2008-08-04
change the permission of the file 
open the terminal and than write 
```
 sudo chmod -R 777 /opt/123

```
this might help u

---

### Post by waterrr on 2008-08-04
can i just do that from user123? or do i need to be another user, bc it didnt work :(

---

### Post by hyper_ch on 2008-08-04
(1) what did you copy in there?
(2) I don't think it's wise to recursively chmod it to 0777

---

### Post by waterrr on 2008-08-04
because i get the response, "operation not permitted"

---

### Post by waterrr on 2008-08-04
i just copied some files into there...a folder of files

---

### Post by hyper_ch on 2008-08-04
what do you require to be in /opt?

---

### Post by waterrr on 2008-08-04
just some files....like .xml files

---

### Post by hyper_ch on 2008-08-04
any reason for them to be in there?

---

### Post by waterrr on 2008-08-04
i would tell you if i knew, i'm just following directions to place them in the /opt directory and work from there

---

### Post by hyper_ch on 2008-08-04
well, this does not really help at all.. so I unsubscribe from this thread.

---

### Post by waterrr on 2008-08-04
anywho...it would be better if someone had explained what they need to exactly know, but i'm still having this problem

---

### Post by Oldsoldier2003 on 2008-08-04
What are you trying to install? A little more information will point people in the right direction and help you get your problem resolved faster.

---

### Post by waterrr on 2008-08-04
it's a platform for a company..wouldn't know how to explain it in terms for you to understand exactly what it is...but that directory involves bin xml and sql files

i just want to be able to execute commands into the /opt directory

---

### Post by waterrr on 2008-08-04
:confused:

---

### Post by oldos2er on 2008-08-04
You can use the command "gksudo nautilus" in a terminal to give you access to /opt.

---

### Post by waterrr on 2008-08-04
i used that to copy the folders, but can i run commands like that?

---

### Post by philinux on 2008-08-04
> **waterrr said:**
> i used that to copy the folders, but can i run commands like that?

you'll need to use 

sudo 

e.g sudo apt-get install whatever

Is there any specific reason that /opt has to be used? If not you could create a directory in your home folder.

---

### Post by waterrr on 2008-08-04
i'm not able to run commands from terminal onto the /opt file...it always says permission denied...is it bc user123 does not have enough permission to access and write to it?

---

### Post by bodhi.zazen on 2008-08-04
What is the name and home page of what you are trying to install ?

Do you have a link to the instructions you are following ?

Sounds like an odd location for your files.

/opt is used to install non-system applications.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/opt.html)

Take a look at permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

[uhelp]community/FilePermissions[/uhelp]

---

### Post by waterrr on 2008-08-04
yes i am installing a non-sys app from what i understand and i do not have a soft copy, its just any command i try to run in /opt gets denied - i didn't know this would get so complicated

---

### Post by bab1 on 2008-08-04
the /opt directory is for "to be installed apps".  I have my Acro8 tar.gz files there, but not the bin files.

---

### Post by philinux on 2008-08-04
> **waterrr said:**
> yes i am installing a non-sys app from what i understand and i do not have a soft copy, its just any command i try to run in /opt gets denied - i didn't know this would get so complicated

Even using sudo as the prefix to the command?

---

### Post by waterrr on 2008-08-04
well these are some of the command lines i have to run in the /opt directory 

*using dummy names

this one is to overwrite the folder with a clean one
```
rm -r /opt/path/to/folder
cd /opt/path/to/folder
tar xvf /tmp/sometarfile.tar.gz
```

then im required to run lines such as
```
sudo vim asdf.xml
sudo vim asdf2.xml
```
in the /opt/path/to/folder

but my permission gets denied from the very first line of rm -r

---

### Post by philinux on 2008-08-04
Thats cos you need sudo like I've been saying. It means superuser and will ask for you password. You cant see it just type it and hit enter.

sudo rm -r /opt/path/to/folder
cd /opt/path/to/folder
sudo tar xvf /tmp/sometarfile.tar.gz

Make sure you get this right cos rm means remove, permanently.

---

