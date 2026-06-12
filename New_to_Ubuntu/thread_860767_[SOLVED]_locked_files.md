---
title: "[SOLVED] locked files"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by matchstich on 2008-07-15
hi,  after i installed 8.04 on this box, i  installed all the files i had on 7.04 to my home .  

cept they are all locked, read only.  read a thread about right clicking

and changing permissions .  i tried that and i still can not do anything with 

the files.

any suggestions will be most appreciated.

thanks

---

### Post by halitech on 2008-07-15
if you used different usernames or the ownership was different, you don't actually "own" the files anymore. To change ownership, you would either need to use nautilus in sudo mode or do it in the terminal with the chown command

---

### Post by UbuntuNerd on 2008-07-15
Try launching root nautilus->
alt + F2 > gksu nautilus
then right click the files > properties> permissions & change them to your user in the drop down list.

---

### Post by matchstich on 2008-07-15
ok, i did alt f2,  went to home and when i changed to read and write

then clicked on apply permissions to files.  all selections made clear

and they are still locked.

am attempting to figure out how chown  works.

thanks

---

### Post by fenian on 2008-07-16
First change the ownership with the chown command,open a terminal and enter...

> sudo chown -R username:username /home/username/

username = your username.

Next set permissions,use the chmod command from the terminal enter...

> sudo chmod 744 -R /home/username/

again username = your username.

---

### Post by matchstich on 2008-07-16
ok, tried the first chown command    and       got this error,

chown: cannot access /home/username/.gvfs": permission denied

thanks

ok, checked i typed in correctly

this time ---got

chown: cannot access home/username/  no such file or directory

---

### Post by K-D on 2008-07-16
I am having a similar problem and a nice chap gave me this message to try out:

In terminal you would type 
Code:

sudo cp /path/of/source/folder/Kris /path/to/destinationHit enter and you will be asked for a password

Also, depending on your view on security, you can create a folder called "Kris" on your main drive using 
Code:

sudo mkdir /path/to/where/you/want/KrisThen you can change ownership of the folder using
Code:

sudo chown -hR [yourusername] /path/to/folder/KrisHope this helps!

i'm going to give it a blast tonight but it could work for you!

---

### Post by t0p on 2008-07-16
> **matchstich said:**
> ok, i did alt f2,  went to home and when i changed to read and write

then clicked on apply permissions to files.  all selections made clear

and they are still locked.

am attempting to figure out how chown  works.

thanks

I always experience this locked-files thing whenever I bring old files into a new install.  The way I fix it is

```
gksudo
```

in terminal, then in the **Run Program** box that appears, type

```
nautilus
```

Now, in the File Manager window that appears, navigate to the files/directories in question, click on **Properties** and change 'em so your username has read/write permissions.

Try it that way.  It worked for me just yesterday!

---

### Post by matchstich on 2008-07-16
hey, i found the problem  there was one file that had create and delete files  where it should have been access files

i changed it and all the other files unlocked.

thanks everyone

---

