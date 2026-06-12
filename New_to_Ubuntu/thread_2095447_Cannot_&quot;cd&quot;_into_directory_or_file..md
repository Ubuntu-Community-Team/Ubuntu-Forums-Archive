---
title: "Cannot &quot;cd&quot; into directory or file."
date: 2012-12-16
forum: New to Ubuntu
---

### Post by leon951 on 2012-12-16
Well before I start I want to apologise for my English, & say that, I done as much "google-ling" as my short attention spam has allowed me and more. Thank you :)

       I cannot "cd" into files, keeps giving me bash error.
I im trying to get "FILE" that is in my desktop, I input 
         cd /home/<user>/Desktop/FILE          
& it gives me 
          bash: cd: /home/<user>/Desktop/file: Not a directory
 I checked the directory multiple times, even dragged the file into the terminal just to check the directory, but I keep getting same error.  I also tried the "./" but that didnt work ether. Also tried being root while using "cd" but no difference.
   What am I doing wrong.
Using ubuntu 12.4 64 bit. Thank you

---

### Post by CharlesA on 2012-12-16
You can't change directory on a file.

Are you trying to open the file?

---

### Post by leon951 on 2012-12-16
Yes im trying to open up the file.
also tried " ls Desktop" to see if it showed the "file" and it did, so it just adds up to the questions.

---

### Post by Vaphell on 2012-12-16
cd = change directory
file is not a directory, so why would cd work? cd is like entering room in the library (changes current location), you can't physically enter the book located there (cding into file).
What to do with the file depends on the kind of file. Executable files can be run after *chmod +x* (./file), text files can be opened with any of text editors (eg gedit file.txt), media files can be played using some media player (eg totem file.avi)

---

### Post by gnusci on 2012-12-16
run this command to see what your are trying to open:

$ file "file-name"

---

### Post by Jvdy on 2012-12-16
if you tried to open a file via terminal 1# you should enter app to open that files with it looks like this:
*gedit /home/<username>/<directory>/<file>*
> thats if your files is a text files
*rhytmbox /home/<username>/<directory>/<file>*
> thats if your file is a sound/music files
*totem /home/<username>/<directory>/<file>*
> thats if your files is a video files 

so you must type an _**appropriated application**_ to open that files with

---

### Post by llamabr on 2012-12-16
part of the problem also is that you're trying to say what you did.  Just copy paste your command, and the output.  It will help us troubleshoot with you.

---

### Post by Bölvaður on 2012-12-17
> **llamabr said:**
> part of the problem also is that you're trying to say what you did.  Just copy paste your command, and the output.  It will help us troubleshoot with you.
no, that is utterly useless. What is useful is the **exact** intentions.

When I mean exact intentions I mean something like this:

"Want to open /home/leon951/Desktop/Diary.doc with some program that will allow me to view and edit it's contents. This file is of MS Word."

Hiding the path (user's home) will increase odds of errors.
Not saying what the end results are supposed to be makes it impossible to guess.

When I get the information I am asking for I will be able, and happy, to help.

---

### Post by Colper on 2013-12-14
> **leon951 said:**
> Well before I start I want to apologise for my English, & say that, I done as much "google-ling" as my short attention spam has allowed me and more. Thank you :)

       I cannot "cd" into files, keeps giving me bash error.
I im trying to get "FILE" that is in my desktop, I input 
         cd /home/<user>/Desktop/FILE          
& it gives me 
          bash: cd: /home/<user>/Desktop/file: Not a directory
 I checked the directory multiple times, even dragged the file into the terminal just to check the directory, but I keep getting same error.  I also tried the "./" but that didnt work ether. Also tried being root while using "cd" but no difference.
   What am I doing wrong.
Using ubuntu 12.4 64 bit. Thank you


For future noob onlookers, I came across this problem.  It was as simple as making sure you have the correct lettering casing.  i.e. I was trying to cd into Documents by typing:  "cd documents",  when it should have been: "cd Documents".  hope this helps.

---

### Post by Iowan on 2013-12-14
Closed.
Thanks for your input, but question was answered in posts 2 and 4.

---

