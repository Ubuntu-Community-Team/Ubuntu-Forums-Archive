---
title: "How to install .bin files"
date: 2010-02-04
forum: Outdated Tutorials &amp; Tips
---

### Post by nubuntee on 2010-02-04
How to install a .bin file running Ubuntu 9.10.

**The Obivous**
- Download .bin file

**User Permission**
- Open Terminal >_

- Login as "root" user to have permission to install. Enter the following in the Terminal: 
[INDENT]sudo su[/INDENT]

( your will now have "root@yourPCname: )

**Prepare the .bin file**
- Permit the .bin file to run
[INDENT]right-click the .bin file > Properties > Permissions Tab > [check] "Allow executing file as program"[/INDENT]

- Copy & Paste your file at the root of the "File System" / Hardrive.
[INDENT]Right-Click .bin file > Copy[/INDENT]
[INDENT]*Navigate*: Open Computer > Open File System > [Paste File Here][/INDENT]

*the location of your file is now "/filename.bin"

**Execute the .bin for install**
- In The Terminal >_ Enter the following:
[INDENT]/filename.bin[/INDENT]
Replace "filename" with the .bin file's name.



That's it. This should run the install of the .bin file. Please feel free to leave feedback if this method worked for you. I'm fairly new to Linux & posted this after struggling my self to find these step by step instructions among the forums.

---

### Post by sivanihonjin on 2010-02-04
Run .bin file in Linux / UNIX

Change the permission of the file you downloaded to be executable. Type the following command:
$ chmod +x file.bin

Start the installation process or run .bin file.Type the following command:
./file.bin

For example if .bin file name is application.bin. Type:
$ chmod +x application.bin
$ ./application.bin

---

### Post by nubuntee on 2010-02-04
those methods didn't work for me. hence my version being different. not saying it doens't work anywhere. just not on my system.

---

### Post by clydeseal on 2010-03-10
I had trouble with installing a bin file. I had downloaded Adobe Air, and when I tried to follow these steps it kept saying no such directory. Finally I moved the bin file to /home/user and it worked.

---

### Post by rejuvenate on 2010-03-10
you need to be in that folder for that where the bin file is there ...you can check ur present path by > pwd and after that > cd directory_nameyou can give the path where the bin file is there and use TAB button after writing partial dir_name that will give whether dir name is correct or not  and use ls to list the contents of the folder...

---

