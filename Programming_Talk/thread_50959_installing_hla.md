---
title: "?? installing hla"
date: 2005-07-22
forum: Programming Talk
---

### Post by grofaz on 2005-07-22
I'm trying to install hla and the instructions state I need to edit a file called ".bashrc" but I can't find the sucker. There's a note that says that Linux filenames beginning with a period don't normally show up in directory listings unless you supply the "-a" option to ls.

Can someone explain to me what this means and how to apply the technique please??

Thank you!

---

### Post by vintem on 2005-07-22
ls stands for list. It gives a list of the files in the current directory, but not all files. There are so-called hidden files (also called invisible files), which aren't shown with ls.
They start with a dot (.)
Hidden files are generally startup files. For example, .bashrc is the startup file that is executed when the bash-shell starts up. Normally you don't need to edit this file, that's why files like this are hidden (so that they don't clutter your directory).
If you need to change your settings for the bash-shell, you can edit .bashrc. 
Every directory (except the root directory) has at least two hidden files: . and ..
.. stands for the parent directory, while . stands for the current directory.
For example, if you are in /home/grofaz/programs and you give the command cd ..
you will change the current directory to the parent directory, which is /home/grofaz
If you repeat cd .. you will be in /home. If you type ls -a in this dierctory you'll get something like:
.  ..  grofaz  anotherfile anotherfile
(ls -a stands for list -all)
Concerning hla, I don't know what precisely you need to add to .bashrc, but if you knowit, you can edit the file with the editor vim:
vim .bashrc
If you never worked with vim, you can choose another editor.

---

### Post by grofaz on 2005-07-22
Hey thank you. You have been most helpful. It is advised to add some path directory lines to the .bashrc file for hla stuff. Otherwise you have to enter manually everytime you try to compile/assemle a program.

Regards

---

