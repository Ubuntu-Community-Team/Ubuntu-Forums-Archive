---
title: "[SOLVED] Deleted Items Folder Query"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by s.fox on 2008-08-09
Hi.

I have a folder inside the deleted items folder that i can't delete.  When i try to delete it i get a permission denied message.   I have checked the properties on all the sub folders and files inside this file and i definitely do have read and write permissions.  I am very confused by this.  If anyone could help me out it would be great.

Thank you for any assistance.

---

### Post by sharks on 2008-08-09
where is the folder and what is the exact name of the folder?

---

### Post by soxs on 2008-08-09
try:
replace path_to_folder with your path
```
sudo chmod -Rvf 755 path_to_folder
```
this should fix any permission issues.
In case it still won't work, do
```
sudo chown $USER:$USER -Rvf path_to_folder
```
Edit:
Note:
In case you only want to kill your whole Trash **forever** use:
```
sudo rm -Rvf $HOME/.local/share/Trash
```

---

### Post by Elfy on 2008-08-09
> where is the folderTrash :)

Try using root nautilus and navigate to the correct trash 

/home/user/.local/share/Trash

```
gksudo nautilus
```

or use a terminal

```
cd ~/.local/share/Trash/files
dir
sudo rm -R nameoffoldertodelete
```

---

### Post by sharks on 2008-08-09
type in terminal gksudo nautilus
it willl make u the root , then delete the files. after deleting please close nautilus and terminal.

---

### Post by s.fox on 2008-08-09
> **soxs said:**
> try:
replace path_to_folder with your path
```
sudo chmod -Rvf 755 path_to_folder
```
this should fix any permission issues.
In case it still won't work, do
```
sudo chown $USER:$USER -Rvf path_to_folder
```
Edit:
Note:
In case you only want to kill your whole Trash **forever** use:
```
sudo rm -Rvf $HOME/.local/share/Trash
```

Thanks for the instructions.  The file i am trying to remove is here apparently: trash:///

What would the path be?  Only reason i ask is because of the ///

Once again thank you

---

### Post by s.fox on 2008-08-09
Did a little looking on the internet and found this snippet of code
```
sudo rm -rf ~/.Trash/*
```

is it safe to run?  will it only delete all the files in my trash?


EDIT:  Thanks i managed to delete the folder :)

---

### Post by soxs on 2008-08-09
> **Ash R said:**
> Did a little looking on the internet and found this snippet of code
```
sudo rm -rf ~/.Trash/*
```

is it safe to run?  will it only delete all the files in my trash?


EDIT:  Thanks i managed to delete the folder :)

In fact it's the same comand as i posted, as ~ = $HOME and v is only an unnecessar option, wihchih makes the whole command verbose, so you actually see when a fil got erased.

---

