---
title: "zip files"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by devilleather on 2008-11-09
hello ,Ok so im new to linux and i have a file on my desktop that i downloaded.I need to know how to get this file installed so i can use the program.  the file on my desktop is called rconnect4-007-source.zip.So i extracted the files to my desktop and it created a folder called Rconnect. In this Rconnect folder contains the files Rconnect.s|n,Rconnect.suo,.Which of these files do i need to execute and how do i run it in a cli. I just want to get the program running. IM learning alot on my own but this seems to be a big problem im having(installing programs,as i dont know how to do it or the commands)THX

---

### Post by MasterSander on 2008-11-09
make sure you downloaded the source. If there are only two files in the folder I'd recheck (make sure you got the source, make sure it unzipped right,...) 

If you've done that, launch up a terminal and navigate to the folder, log in as root (sudo -i)

type ./configure --> that will check if you got all the correct librairies installed for compiling. if that gives you errors, get the missing librairy.

If everything was allright type make --> this will compile the source into a program

Now you've already compiled the program, now we have to move it to the right folder, type make install.

---

### Post by devilleather on 2008-11-09
when i type ./configure -->  I get 
-bash: syntax error near unexpected token `newline'
root@brandon-desktop:~#

---

### Post by devilleather on 2008-11-09
I think I might have been in the wrong folder. The file is on my desktop so is that the folder i need?

---

### Post by MasterSander on 2008-11-09
cd /home/yourname/desktop --> that should get you on your desktop. Type ls and check for the folder, then navigate to the folder and type ls and then type ./configure, post some output here so I can check if you're doing it allright

---

### Post by devilleather on 2008-11-09
ok when i type ls    the file is not in the list,but i see the file on my desktop

---

### Post by devilleather on 2008-11-09
ahh im such a newb when i typed desktop i should have typed Desktop i forgot it is case sensitive.

---

### Post by Ryadt on 2008-11-09
Why are you login as root?

---

### Post by devilleather on 2008-11-09
root@brandon-desktop:/home/brandon/Desktop# ./configure
-bash: ./configure: No such file or directory

---

### Post by gandaran on 2008-11-09
does the package contain a readme file with instructions? or can you post the link for downloading the package so we can have a look on how to install

---

### Post by devilleather on 2008-11-09
root@brandon-desktop:/home/brandon/Desktop# ./configure
-bash: ./configure: No such file or directory

---

### Post by devilleather on 2008-11-09
here is the url. I have the rconnect4-007-source.zip on my desktop

[http://sourceforge.net/project/showfiles.php?group_id=243438](http://sourceforge.net/project/showfiles.php?group_id=243438)

---

### Post by gandaran on 2008-11-09
thats a .exe windows program, wont run in linux!

---

### Post by devilleather on 2008-11-09
[http://sourceforge.net/project/showfiles.php?group_id=243438](http://sourceforge.net/project/showfiles.php?group_id=243438)

Ihave the rconnect4-007-source.zip on my desktop

---

### Post by devilleather on 2008-11-09
ahh so having the source doesnt mean it can be run in ubuntu. Ok thx

---

### Post by gandaran on 2008-11-09
sorry I downloaded the wrong file, but I still believe this program is for windows, I'll have a look again
 
edit; it's for microsoft only

---

### Post by devilleather on 2008-11-09
OK so to my next problem (i hope im in the right section for this). Im trying to install crysis wars for ubuntu. I have the linux server files on my desktop which u can get here [http://www.fileshack.com/file.x/13226/Crysis+Wars+Linux+Server](http://www.fileshack.com/file.x/13226/Crysis+Wars+Linux+Server). Im lost and dont know where to start. Do i have to use wine?

---

