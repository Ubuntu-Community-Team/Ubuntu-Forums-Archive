---
title: "shell scripts"
date: 2010-02-15
forum: Programming Talk
---

### Post by ryanf4321 on 2010-02-15
In one of my classes, we are beginning to write some shell scripts. Since I am fairly new to linux, let alone shell scripts, I know only the basics. One of the questions is how to make a directory that is 100 levels deep, out of /home. The directories are all named the same.

Can anyone give me some hints on how to do this? Does it involve a loop?

---

### Post by LoneWolfJack on 2010-02-15
define a string that contains your starting folder. then write a loop that will append a new folder name at the end of that string and use mkdir to create this directory.

---

### Post by djurny on 2010-02-15
> **ryanf4321 said:**
> In one of my classes, we are beginning to write some shell scripts. Since I am fairly new to linux, let alone shell scripts, I know only the basics. One of the questions is how to make a directory that is 100 levels deep, out of /home. The directories are all named the same.

Can anyone give me some hints on how to do this? Does it involve a loop?

some extra hints:
* look up the 'seq' command
* look up the 'mkdir' command ('-p' option)
* look up the man page of your favorite shell 
  > string manipulation
  > for loops
hope that helps :)

---

### Post by Psycho.mario on 2010-02-15
something like this:

i=0
if [ $i -lt 100 ]
then
mkdir directory
cd directory
echo $i | bc
else
exit
fi 

The first line sets the variable 'i', then the if statement checks if the i variable is less than 100, if it is then it creates a new directory, changes into that directory, and makes the i variable one bigger. if the i variable is more than or equal to 100 then it exits

---

### Post by bapoumba on 2010-02-16
ryanf4321, please be aware we won't support homework here. Hints are fine, so I'm leaving the thread open. I'll move it to PT.

---

### Post by ryanf4321 on 2010-02-16
cool, thanks for the hints everyone. 

bapoumba, sorry, i didn't wasn't sure where else to post this.

---

