---
title: "Terminal Questions"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by mferarri on 2012-03-03
Hi Ubuntu Forums,

I'm beginning to learn to use the terminal now. Just a few questions:

1.How do i undo a name change (i accidently renamed a .deb file instead of moving it into another folder)

2.How do i move a file without renaming it (i.e. mv example.deb folder2 would rename it, not move it into there)

3.Where can i find keyboard shorcuts for nano?

4.How do i get a list of programs you already have to run in terminal (e.g.1. i was trying to open a pdf in adobe reader 9, but i dont know what to type. e.g.2. for images i would type: feh *jpg to open images)

5.Why is it when i typed in sort *.rar a whole bunch of gibberish started flying across the screen?

6.Pressing tab dosent fill in the rest of the files name? if i type ls and see the file that i want, begin typing that file name and press tab, it dosen't autofill? 

7.How do i select a line, or a word in the terminal and in nano?(like in MS word it would be shift+end, and ctrl+leftarrow)

---

### Post by kevdog on 2012-03-03
1. Can't really undo, just rename it again with the mv command
2. Use mv.  If you have file name file_x and want to move it to the directory named directory, it would be mv file_x ~/directory/ or something like that -- it does not have to be mv file_x ~/directory/file_x
3. Dont use nano so I don't know
4. pdf can open with evince
5. Not sure
6. Not sure why tab doesn't work for you.
7. Don't use nano.

---

### Post by _0R10N on 2012-03-03
1.- You cannnot. You have to change it again to its original name.
2.- If you want to move a file to another folder without renaming it, just make sure that the second argument given to the move command finishes with the folder name where you want it to be located.
4.- Press <TAB> two times.
6.- Probably you don't have permission to perform the given operation on those files.

---

### Post by papibe on 2012-03-03
Hi mferarri.

> **mferarri said:**
> I'm beginning to learn to use the terminal now. Just a few questions:

1.How do i undo a name change (i accidently renamed a .deb file instead of moving it into another folder)

2.How do i move a file without renaming it (i.e. mv example.deb folder2 would rename it, not move it into there)
Take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1934278&highlight=autocompletion") where the same problem and a solution is discussed (autocompletion is your best friend).

> **mferarri said:**
> 5.Why is it when i typed in sort *.rar a whole bunch of gibberish started flying across the screen?
'sort' read text files and sort its content. Why do you want to do? List the files may be? if so, try 'ls *.rar'.

> **mferarri said:**
> 6.Pressing tab dosent fill in the rest of the files name? if i type ls and see the file that i want, begin typing that file name and press tab, it dosen't autofill? 
Only when there's no doubt what to complete. It may require you to enter several letters before it works.

> **mferarri said:**
> 7.How do i select a line, or a word in the terminal and in nano?(like in MS word it would be shift+end, and ctrl+leftarrow)
If you are using a terminal from a GUI environment you can use the mouse's left click to copy/paste text.

Hope it helps, and tell us if you need more tips.
Regards.

---

### Post by mferarri on 2012-03-03
Thanks for replying everyone,

1.solved. Undo rename? The name the name is gone forever now i guess. lol.

2.solved. thanks papibe,"If the second argument does not exists 'mv' acts as rename." - this makes sense to me now

3.solved. found it. 

[http://staffwww.fullcoll.edu/sedwards/Nano/NanoKeyboardCommands.html]("http://staffwww.fullcoll.edu/sedwards/Nano/NanoKeyboardCommands.html")

4.solved. found out that using the command: "gnome-open" can open any file. woot!

5. solved. Thanks again papibe. "'sort' read text files and sort its content". This was just an experiment to see what sort does.

6.solved. I figured this one out. you have to have a command written before it, before it can autocomplete. (e.g. longname.txt does not auto complete, whereas mv longname.txt works)

7.solved in Q4.


all solved thanks guys.

---

