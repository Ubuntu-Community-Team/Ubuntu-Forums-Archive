---
title: "[SOLVED] navigate to a terminal"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by Madwida on 2008-08-26
Hi 

I am getting better and better at the terminal--and actually enjoying it.  But I have a very fundamental question: What do I do when I am instructed to "Navigate to the folder you have placed X in.  Now, run these two commands:"?    

I know how to open a terminal, do various commands, but this is not clear.  

Thanks a lot

---

### Post by silverglade00 on 2008-08-26
Let's say you downloaded a file to your desktop as part of the instructions. Then it says to open a Terminal and navigate to where you downloaded the file. You would type:

```
cd /home/madwida/Desktop
```

or wherever you saved the file. If you are using Firefox, I believe that it defaults to the desktop anyway. It just means to cd (change directory, which is the old school word for folder) to that folder in the terminal.

---

### Post by Joeb454 on 2008-08-26
Just run ```
cd /path/to/your/folder
```

---

### Post by halitech on 2008-08-26
to add a little further, normally the terminal opens in your home folder (ie /home/madwida) to if you wanted to go to the desktop, you can simply type```
cd Desktop
```

if at any time you want to go back to your home folder, just simply type cd

in case you didn't know, folder names in Linux are case sensitive so desktop is not the same as Desktop

---

### Post by Madwida on 2008-08-26
Hi 

Many thanks!!

---

### Post by barbedsaber on 2008-08-26
you can also type ```
cd ..
``` to go up one level in your file system (eg, go from your music folder, to your home folder)
you can also use ```
ls
``` to list the things that are in the folder you are in, and ```
pwd
``` to **p**rint **w**orking **d**irectory, which basically means find out where you are, for if you get lost.
The prompt (bit at the beggining) tells you a fair bit as well, for example
```
harry@ubuntu:~$
``` tells me I am logged in as harry. my computer is called ubuntu. the Tilda (~) tells me that I am in my home folder (the Tilda sign (~) is often used for home, in fact, you can type cd ~ to go to your home directory). the dollar sign ($) tells me I am not the root user.

---

### Post by sisco311 on 2008-08-26
type:
```
pwd
```to print the current/working directory.

---

### Post by Elfy on 2008-08-26
You can also use tab to autocomplete so if you were at home then cd D followed by tab would probabaly get to Desktop unless you had another folder starting with D, try it.

---

### Post by Madwida on 2008-08-26
Thanks everyone for the fast and easy to follow replies.  The terminal's getting easier and easier

---

### Post by barbedsaber on 2008-08-26
If your problem is fixed, can you please mark this thread as solved
all you have to do is click thread tools (top right of this page)
then mark thread as solved.
It makes the lives of all the people that help a lot easier.
thanks! :)

---

### Post by drubin on 2008-08-26
To add to what every one has written. 
you can always type 
```
cd ~/Desktop
```

the ~ refers to your home folder of the current logged in user. It is nice when you do not want to have to type /home/username.

Something you might find handy is 
```
ls -lh
```

Give you a listing of the files/folders in the current dirctory, and give the sizes in Human readable format so in kb and MB instead of huge byte sizes. 

If you want to know how to use other commands  run this
```
man ls
```
```
man COMANDNAME
```

and it will give you the info/parameters you can use with it. (Some times can be confusing just stick with it)

---

### Post by barbedsaber on 2008-08-26
Oh yeah, I forgot to mention man pages, (no, they are not about men, man is short for **man**ual

---

### Post by Nythain on 2008-08-26
i've also found that googling "<command> man page" will result in a much easier to read and navigate online version of the man page :)

---

