---
title: "[SOLVED] how do i delete multiple files with (copy) on them"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by stinger30au on 2008-11-03
i have a directory with a few hundred .zip files

i was using  nautilus to copy/paste the files to another directory


in my haste i actually pasted them in to the same directory i was trying to copy from in the first place


so now i have got this

program (copy) . zip

as well as the original


program.zip

in my directory. how do i delete all the (copy) of the zip files i have made???

in windows xp if i did something silly like this i could use a list view and arrange the files by name and it would make the files names like this

copy of program.zip

i coudl then easily highlight all the copy files and delete them.
i have tried a few different settings on nautilus and no joy.

i have a suspicion i can do it from the command like in a simple one line command but im not sure what it is

i suspect the command will be something like

del *(copy).zip 

but dont know for sure. can someone please help me out.
Thanks:confused:


i forgot i had xp in virtual box so i fired it up and used the command line and did a 

del *(copy).zip

and it works, but how do i do it natively in linux at command line?

---

### Post by igknighted on 2008-11-03
'rm -f *copy*' should do the trick, as long as none of the names has copy in it.

---

### Post by Sand Lee on 2008-11-03
Here, you want to move all those files to a directory, then delete them in a GUI just to make sure you're not removing anything you don't want to (you can't undo rm!)

cd ~/whatever-that-directory-is-with-the-files
mkdir deletes
mv *"copy)" deletes

then delete that directory with nautilus :guitar:

---

### Post by wardrich on 2008-11-03
Assuming there are no directories that need to be removed, you'd probably be safer off going into the directory with the files in question and doing:

rm *copy*

by removing the "force" switch, it will actually ask you if you want to erase the each file one at a time, that way you won't accidently erase something you don't mean to.  rm is a permanent command, but if you don't do the -f on it, you should be fine.  For the record -r is only for a recursive removal, so if you don't have any directories in question, don't bother with it.

---

### Post by stinger30au on 2008-11-03
thanks for the feed back guys, your all life savers!!!

greatly appreciated

---

