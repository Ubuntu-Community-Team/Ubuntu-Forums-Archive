---
title: "root problem... can somebody explain?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by afbuntu on 2008-11-10
i have a mp3 player that i recently open in windows. i have reason to believe that once i open this mp3 player in ubuntu, i found some folder which i believe is made by virus in windows. i try to remove it by deleting it but i dont have permission. i check the properties and it said there permission by group root only.

1. what does this mean? what is root?

2. can i login as root? if yes how?

---

### Post by Paqman on 2008-11-10
> **afbuntu said:**
> i found some folder which i believe is made by virus in windows.

That's possible, but unlikely. It's more likely to be a hidden folder that just doesn't show up in Windows.

What is the folder called and what does it contain?

---

### Post by beercz on 2008-11-10
Does [this]("https://help.ubuntu.com/community/RootSudo") help?

---

### Post by mr.v. on 2008-11-10
Ubuntu discourages using a root account. Root is the "administrator" account in linux.

The way to get access to root is through use of the "sudo" command.

If you want to delete that folder, open a terminal window and type:

```
sudo rm -r /path/to/folder/to/remove
```

and it will prompt you for your password. Usually the sudo password is the same password on the default account.

---

### Post by Bölvaður on 2008-11-10
uh rm is for removing files, rmdir is to remove folders.

so:

> gksudo nautilus
is the beginners best friend AND WORST ENEMY. Be warned that you are given godlike power like in windows, which might result in broken system if the files are necessary for the integrity of the OS, filesystem or even device to function.


I would not suggest deleting these files. Unless if you get consent from the forums that those files are not normal.

---

### Post by Sarmacid on 2008-11-10
> 1. what does this mean? what is root?
Root is the account with full power on unix systems. Usually it's not adviced to work with it, that's why we have sudo.

So as mrv.v. posted use```
sudo rm -r /path/to/folder/to/remove
``` in a terminal to remove the folder, or you can right click it, go to properties, in the permissions tab give yourself read/write permissions, and now you should be able to delete it.

---

### Post by mr.v. on 2008-11-10
> **Bölvaður said:**
> uh rm is for removing files, rmdir is to remove folders.


uh try it.

I think you'll find out you're wrong. ```
man rm
``` will elaborate more fully.

rm -r is, in some ways, better than rmdir as rmdir will not remove a directory if there are files in it, while rm -r will both delete files in the directory and the directory itself (it's therefore more dangerous as well).

---

### Post by afbuntu on 2008-11-10
thank you all.

---

### Post by Ptero-4 on 2008-11-11
Just remember that when using the command line delete tool you need to check your syntax carefully. A small mistake and you might end up bricking either your OS installation or the mp3 player's filesystem.

---

