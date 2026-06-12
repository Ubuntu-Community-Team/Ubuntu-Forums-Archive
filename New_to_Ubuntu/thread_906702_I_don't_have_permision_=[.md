---
title: "I don't have permision? =["
date: 2008-08-31
forum: New to Ubuntu
---

### Post by RadiationHazard on 2008-08-31
ok so I'm trying to add files to my server and delete stuff that was installed when I installed LAMP and when I right click on it I can't delete this folder and I can't make new files and folders. I know I can type sudo something in the terminal and it will open another window that give me full permission to add and delete what I want. does anyone know what it is?

---

### Post by halitech on 2008-08-31
the reason you can't create or delete files/folders is because you don't 'own' them, they are owned by root.

be *VERY* careful when using this command as it can really mess up your system
```
gksu nautilus
```
and make sure you close it when done

---

### Post by porchrat on 2008-08-31
Use the command line as this is the easiest way to give yourself (and every user logging into that system) full permissions to do anything with a file or folder:

If it is a file then type this:

```
sudo chmod 777 path_to_file
```

where "path_to_file" is the location of the file you wish to access.  Note that this command will give full read, write and execute permissions to all users logged onto that computer.

If you wish to do the same thing, but with the entire content of a directory then type this:

```
sudo chmod -R 777 path_to_directory
```

if you merely want to change the ownership of the file or folder then type this:

```
sudo chown username:username path_to_file_or_directory
```

use the "-R" if you want to change ownership of the entire contents of a directory.

hope that helps.

---

