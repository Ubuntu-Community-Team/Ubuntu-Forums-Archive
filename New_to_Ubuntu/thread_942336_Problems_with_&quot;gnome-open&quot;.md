---
title: "Problems with &quot;gnome-open&quot;"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Shaggy_edu on 2008-10-09
Hey Everyone,

Im new to the forums and first, let me say you guys really do know your Ubuntu and/or coding. I am really impressed and excited that I found a site dedicated to helping others in their quest.

My question has already been asked before but I didnt get any real results with the solutions that were given.

Using the Terminal, how do you open files? I dont have any problem opening folders but, opening any single files WITHIN the folder is where my problems start. I have an Ebook saved in a folder named "Ebooks" heh.:) Where I try and open the file in the terminal I get something like...

Error showing url: The location or file could not be found.

Whats missing?


It may not be that important but, im just trying to learn the ways around the terminal. Any help will be awesome.


Thanks.

---

### Post by neilengineer on 2008-10-09
open file in terminal in Linux, you should use editers for terminal,like vim.

Open file1.txt with vim using:
$vim file1.txt

BTW: for Ebooks there may not be any editers or viewers in terminal.

---

### Post by Shmook on 2008-10-09
I'm not sure what extension your e-book is, but I had one that was a .chm and had to install chmsee from Add/Remove under Apps. Then I just opened it thru the graphical file manager. 

In Add/Remove search for "chm" and a bunch of readers will show up :guitar:

---

### Post by Shaggy_edu on 2008-10-09
The Ebook is a PDF. It opens fine if I just go through the GUI and click. I was just trying to open it up WITH the terminal. Not in it. Maybe a copy and paste of my terminal will help?


yoshi@yoshiubun:~$ cd Documents
yoshi@yoshiubun:~/Documents$ ls
Ebooks  Pictures
yoshi@yoshiubun:~/Documents$ cd Ebooks
yoshi@yoshiubun:~/Documents/Ebooks$ ls
Beginning Linux Programming.pdf
yoshi@yoshiubun:~/Documents/Ebooks$ gnome-open Beginning Linux Programming.pdf
Error showing url: The location or file could not be found.
yoshi@yoshiubun:~/Documents/Ebooks$

---

### Post by neilengineer on 2008-10-13
> **Shaggy_edu said:**
> yoshi@yoshiubun:~/Documents/Ebooks$ gnome-open Beginning Linux Programming.pdf
Error showing url: The location or file could not be found.
yoshi@yoshiubun:~/Documents/Ebooks$


The command was not right, you should use the following command(a "backslash" before everything "space"):
$gnome-open Beginning\ Linux\ Programming.pdf

---

