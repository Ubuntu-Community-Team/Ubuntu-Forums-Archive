---
title: "can anyone help me in this plz ? :("
date: 2012-04-28
forum: Programming Talk
---

### Post by Tamik on 2012-04-28
1. Write a script called “myls” that will perform similarly to how the ls command does. Start by making myls print out all files in the present directory.
2. Next, make the script print out all files in a different directory.
3. Next, make the script prompt the user to enter a directory (interactively) and print all files in the specified directory.
4. Now, enhance the script so that it will print * beside each executable file in the directory, and d beside directories. It should also print out the read/write permissions as r and w (if you have them – if not, it should just print a - instead).
5. Finally, to make your myls that much more professional looking, modify it so that it will take the directory as a command line argument, rather than an interactive prompt. In other words, you should be able to run it as:
./myls /home/instructor/files

---

### Post by oldfred on 2012-04-28
moved to programming, but this looks like homework.

You did agree to the Code of conduct when you signed up.

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
> 

[LIST=1]
[*]While we are happy to serve as a resource for hints and for asking  questions when you get stuck and need a little help, the Ubuntu Forums  is not a homework service. Please do not post your homework assignments  expecting someone else to do it for you. Any such threads will be taken  offline and warnings or infractions may be issued.
[/LIST]


---

### Post by Habitual on 2012-04-28
Tamik:

What have you written so far?

---

### Post by Tamik on 2012-04-29
okay i'll write what i wrote in here 
1- nano myls.sh
then inside the nano
```
#!/bin/bash
ls
``` 
then save
chmod +x myls.sh
./myls.sh
2- nano myls.sh
```
#!/bin/bash
ls -R
```
save 
./myls.sh
3- nano myls.sh
```
#!/bin/bash
mkidr direc
echo " enter the name of the directory you want "
sleep1
read direc
if test -d "$direc"
then 
cd direc
ls $1
fi 
exit 0
```
save and ./myls.sh
4- nano myls.sh
```
#!/bin/bash
ls -fl > mine
if test -d "$mine"
then 
echo "$mine d"
exit 1
elif test -x "$mine"
then
echo "$mine *"
exit 1
elif test -rw "$mine"
then 
echo " $ls -l"
exit 1
elif test -f "$mine"
then
echo "$mine a"
exit 1
```
save and ./myl.sh 


so what do u think is it right or not ??? if not plz help me :(

---

### Post by Habitual on 2012-04-29
/home/**instructor**/files certainly looks like an assignment.
Your 'requirement" looks like a variation of this [assignment.]("http://www.cs.uwyo.edu/%7Ebskari/courses/fall10/cosc4750/lab2.html")

---

