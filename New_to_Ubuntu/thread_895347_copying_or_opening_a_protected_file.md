---
title: "copying or opening a protected file?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by phantomjoker on 2008-08-20
Hi

I've just attempted to recover a bunch of deleted files, and i have been left with protected file (which apparently i don't have permission to touch)

How do i either open these, or copy them to a external so i can transfer them to a windows computer?

thanks

---

### Post by iaculallad on 2008-08-20
> **phantomjoker said:**
> Hi

I've just attempted to recover a bunch of deleted files, and i have been left with protected file (which apparently i don't have permission to touch)

How do i either open these, or copy them to a external so i can transfer them to a windows computer?

thanks

Using the terminal:

```
sudo cp -R /location_1/folder /location_2/folder
sudo cp /location_1/filename.ext /location_2/filename.ext
```

Or simply:

```
gksudo nautilus
```

and begin browsing for the files you want copied and save it to other locations.

---

### Post by bryncoles on 2008-08-20
or/ open a terminal and type the following:

```
chmod u+rw -R FILEPATHTOPROTECTEDFILES
```

that'll chsange the permissions (chmod) for the user (thats you - u) to give read and write access (rw) recursively (R) - to everything within the folder too. 

you can get the file path easiest by just dragging and dropping the folder into the terminal once you have types 'chmod u+rw R ' (dont forget that space after the R)

*edit*

good call too late, added the dash above (for clarity)

---

### Post by Too Late on 2008-08-20
> **bryncoles said:**
> (dont forget that space after the R)
Space is not enough. ;-) It must have hyphen, too (or is it called dash?):```
-R
```

---

### Post by phantomjoker on 2008-08-20
WOW, i even couldnt do that...

> mckenzie@ubuntu:~$ chmod u+rw -R /home/mckenzie/e1
chmod: changing permissions of `/home/mckenzie/e1/recup_dir.1': Operation not permitted
chmod: cannot read directory `/home/mckenzie/e1/recup_dir.1': Permission denied
chmod: changing permissions of `/home/mckenzie/e1/recup_dir.2': Operation not permitted
chmod: cannot read directory `/home/mckenzie/e1/recup_dir.2': Permission denied
mckenzie@ubuntu:~$ 

---

### Post by phantomjoker on 2008-08-20
oops - i forgot sudo :S

---

### Post by Bliepo32 on 2008-08-20
Then place sudo in fornt of it. So it becomes:

```

sudo chmod u+rw -R /home/mckenzie/e1

```

---

### Post by phantomjoker on 2008-08-20
No - still didn't work... It just went back to the begining terminal screen $...

but i still cant open the folders

---

### Post by Bliepo32 on 2008-08-20
And you wanted to delete the folder?

---

### Post by t0p on 2008-08-20
> **phantomjoker said:**
> No - still didn't work... It just went back to the begining terminal screen $...

but i still cant open the folders

Did you get an error message?

If you don't get an error message, it generally means the command succeeded.

---

### Post by CypherHackz on 2008-10-06
Open Terminal and go to the folder which has the protected folders. Then type this:

```
sudo chmod -R 777 *
```

This will CHMOD all files/folders to 777. And now you can open/edit/delete whatever you want with the unprotected folders.

-cypher.

---

### Post by jerome1232 on 2008-10-06
meh, I think your just not the owner, run this last command it'll make you the owner (without giving every1's dog the abiltiy to modify the files
```
sudo chown $USER:$USER -R /home/mckenzie/e1
```

chown changes ownership
chmod changes permisions

---

