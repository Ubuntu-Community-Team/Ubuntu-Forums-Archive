---
title: "Learning C with Ubuntu"
date: 2015-01-22
forum: New to Ubuntu
---

### Post by trent5 on 2015-01-22
I'm not asking help for HOW to write C code, I need help using Ubuntu to make C code. (This is my first time using Ubuntu)

This is a class assignment to learn how to use this stuff, so what I have to do is download a .c file from the class website and modify the file to make working C code.
I downloaded the .c file and it is setting on my desktop. I changed the name (as requested by teacher) to "_HW1-2.c_".
Now, the assignment tells me this:



**You should open a “terminal window” to run gcc under Linux. Use the linux command****cd to change your current working directory to the directory in which you placed the shell**
**program. For example,**
**> cd ~/Documents/2035/hw1**
**You can list the files in that directory using**
**> ls -la**
**You can copy a file using cp or rename a file using mv (move a file to a new file). For example:**
**> cp HW1-2-shell.c HW1-2.c**



I have the terminal window open but after that I have no idea what this is saying or what it means. Please help me understand.

---

### Post by newbie-user on 2015-01-22
Okay, let's go line by line.
[LIST]
[*]***cd ~/Documents/2035/hw1*** This means to change directory ([COLOR="#40E0D0"]cd[/COLOR]) to your home folder ([COLOR="#40E0D0"]~[/COLOR]) [COLOR="#40E0D0"]/[/COLOR] a folder within your home folder ([COLOR="#40E0D0"]Documents[/COLOR])[COLOR="#40E0D0"] /[/COLOR] a folder within the Documents folder ([COLOR="#40E0D0"]2035[/COLOR]) [COLOR="#40E0D0"]/[/COLOR] a folder within the 2035 folder ([COLOR="#40E0D0"]hw1[/COLOR])
[*][B][I]You can list the files in that directory using
> ls -la[/I][/B] This means to list ([COLOR="#40E0D0"]ls[/COLOR]) all the contents of your current location with the attributes to show long format ([COLOR="#40E0D0"]-l[/COLOR]) and to show all contents including hidden files ([COLOR="#40E0D0"]a[/COLOR])
[*][B][I]You can copy a file using cp or rename a file using mv (move a file to a new file). For example:
> cp HW1-2-shell.c HW1-2.c[/I][/B] This means you can copy (cp) a file to another location to make a duplicate or move (mv) the file. The command as shown is making a copy of the file with a new name by using the cp command: cp [file to copy from] [file to copy to]. The command is making a copy ([COLOR="#40E0D0"]cp[/COLOR]) of the file [COLOR="#40E0D0"]HW1-2-shell.c[/COLOR] and naming the duplicate as [COLOR="#40E0D0"]HW1-2.c[/COLOR]
[/LIST]
So now that you've already renamed your file, you need to move it to the assigned location, which is ~/Documents/2035/hw1. To do this, use the move command (mv). The command will be ***mv ~/Desktop/HW1-2.c ~/Documents/2035/hw1/***
Translation: move the file called HW1-2.c, which is located in home (~) / Desktop to the new location in home (~) / a folder within your home folder (Documents) / a folder within the Documents folder (2035) / a folder within the 2035 folder (hw1)

---

### Post by whitesmith on 2015-01-22
Have a look at the second item in my sig line. I think this will take care of your problems with the command line, which we call a shell. Cheers!

---

