---
title: "Recycle bin concept in linux"
date: 2011-05-24
forum: Programming Talk
---

### Post by Blackbug on 2011-05-24
I was wondering if there is any thing similar to 'Recycle Bin' in linux?
From where you can restore deleted files in case you have deleted them by some typing mistake or in hurry?

---

### Post by simeon87 on 2011-05-24
In Ubuntu there is something like that, it's called Trash. You can view the contents by clicking the trash can icon on your desktop or by going to trash:///

---

### Post by NovaAesa on 2011-05-24
There's the "Trash" if you delete something using Nautilus, but if you use rm, it's not trivial to restore a deleted file.

---

### Post by lalitpratap on 2011-05-24
In ubuntu there is folder called trash, which can be located at any of the location according to your user priveleges..
 
if logged in as normal user :
 
 
**/home/<user_name>/.Trash**
 
if logged in as root user or super user :
 
**/root/.Trash**
 
if delete some data it goes there similar to recyclebin in windows.
you can also restore your data from this trash folder.

---

### Post by Grenage on 2011-05-24
> **Blackbug said:**
> I was wondering if there is any thing similar to 'Recycle Bin' in linux?
From where you can restore deleted files in case you have deleted them by some typing mistake or in hurry?

Unfortunately (or fortunately), no.  You really have to be of clear mind when you're administering a system with a terminal.  You could of course get a script and use that instead of rm; it could move the files to a directory of your choice, rather than delete them.  Some may already exist.

I once overwrote 80GB of data with a sleep-deprived command; it's not something I've repeated!

---

### Post by Blackbug on 2011-05-24
well, i am using SUSE 11 at present at work so if anything such available for the same, and strictly console based work.
 
I will try suggestions regarding ubuntu at my home pc.

---

### Post by Blackbug on 2011-05-24
well i did something similar, i had overwritten and also deleted around 20 c++ classes while executing a script. Thanks to clearcase i could retrieve the original version, but not with my changes. So, I had to again rewrite the code.
 
Thus, I was really curious to know if there is anything to restore/undo in unix/linux.

---

### Post by Grenage on 2011-05-24
> **Blackbug said:**
> well i did something similar, i had overwritten and also deleted around 20 c++ classes while executing a script. Thanks to clearcase i could retrieve the original version, but not with my changes. So, I had to again rewrite the code.
 
Thus, I was really curious to know if there is anything to restore/undo in unix/linux.

Not particularly forgiving, is it? ;)

---

### Post by ssam on 2011-05-24
i have seen people make wrappers for rm that turn it into a move to trash command. might be useful in somecases, but really annoying in others.

there are also a few programs that do undeletion of files. unfortunately this is only easy to do on very basic file systems (like fat).

having a good incremental backup system in place is probably the best thing to do. it will protect you from a wider range of disasters.

---

### Post by dwhitney67 on 2011-05-24
The "rm" command used to remove files supports many options; thus trying to re-implement it do something as trivial as placing deleted files into a "trash" area is not an easy task, but at the same time, it is not impossible.

Take for example this simple bash function; it handles the "deletion" of a single file, by copying it to the Trash bin, and then removing it.
```

# Replace "rm" command so that files are disposed to the
# user's Gnome trash can.
#
rmfile()
{
   type=`/usr/bin/stat --printf="%F" "$1"`

   if [ "$type" == "directory" ]; then
        echo -n "rm: cannot remove \`"
        echo -n $1
        echo "\`: Is a directory"
   else
        dir=`/usr/bin/dirname "$1"`
        file=`/usr/bin/basename "$1"`
        info=${HOME}/.local/share/Trash/info/"$file".trashinfo

        cd "$dir"

        /bin/cp "$file" ${HOME}/.local/share/Trash/files
        /bin/rm -f "$file"

        echo "[Trash Info]"                > "$info"
        echo "Path=$PWD/$file"            >> "$info"
        echo "DeletionDate=`date +%FT%T`" >> "$info"

        cd "$OLDPWD"
   fi
}

```
Preferably, this function would be nice if it supported the -r, -f, and the -i options that are supported by "rm".

---

### Post by Blackbug on 2011-05-24
well decent suggestion.
its good to use this script to delete any object.
 
thanks..

---

### Post by Mr. Shannon on 2011-05-24
A realy easy solution to make rm move files to the trash bin is to install **trash-cli** and then put this line in your bashrc file
```
alias rm='trash'
```
Hoever, if you use
```
sudo rm file
```
the file will not go to the trash it will be permanently deleted (I think).  Also, if you wan't to permanatly remove a file as a regular user then just type
```
\rm file
```
The backslash overrides the alias.

Note: the recursive option works with trash, I'm not sure about any of the others though.

---

### Post by slavik on 2011-05-24
ext3cow for the win!

---

### Post by Blackbug on 2011-05-25
thanks for the helping on this
still the post in open..for any further new approaches..

---

### Post by drifter08 on 2011-12-31
> **Mr. Shannon said:**
> A realy easy solution to make rm move files to the trash bin is to install **trash-cli** and then put this line in your bashrc file
```
alias rm='trash'
```

**DO NOT** alias *rm *to *trash*. That is a bad practice that breaks POSIX and will likely cost you if the alias breaks, or you're on a system that doesn't have the alias. It will also cause scripts to break, or behave unintuitively recycling files that should be deleted.

**INSTEAD**, install **trash-cli**, but DO NOT alias *rm* to it. Make a habit of deleting files with *trash*, and use *rm* when (and ONLY when) you decide to delete a file permanently.

The function and meaning of *rm *is to permanently delete files, freeing disk space. Getting used to feeling safe with *rm* to delete files is madness.

---

