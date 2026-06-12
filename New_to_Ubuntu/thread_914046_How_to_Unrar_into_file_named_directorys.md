---
title: "How to Unrar into file named directorys"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by PoseidonOSU on 2008-09-08
I have like 300 rar files in one directory. It is very tedious to copy the name of the file. then unrar it to a new directory with the file name. Ther has t obe a faster way to do this.  

I want:
balbalbla.rar uncompressed into a folder named blablabla

Any idea on what program to us or a script?

thanks
E

---

### Post by pofigster on 2008-09-08
A shell script ought to handle this pretty easily, but I've never written a script that allows the user to specify inputs...

Seems like you could though, anybody know for sure how this could be done?

---

### Post by d3synguy on 2008-09-08
Well, I don't have my Ubuntu up and running yet, but in Windows you can usually right click on the .rar file and you are presented three choices for unpacking: "Extract files", which opens up a dialog box where you can choose all sorts of paths and options, "Extract here", which will unpack all the files in the current location, or "Extract to blablabla\", which will create a new folder in the current location with the same name as the .rar file you are unpacking.

Sorry, disregard the above -- I misunderstood your post.

---

### Post by fauzie on 2008-09-08
I'm not sure about rar files ... but I guess it should be something like:

1. Go to the directory with 300 rar files, assuming it is inside youre $HOME dir:
cd ~/blablabla1

2. unrar all of them there
unrar *.rar

3. make a new directory
mkdir ~/blablabla2

4. move all of your .rar files there
mv *.rar ~/blablabla2

---

