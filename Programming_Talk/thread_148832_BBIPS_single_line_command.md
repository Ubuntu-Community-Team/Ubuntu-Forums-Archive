---
title: "BBIPS single line command?"
date: 2006-03-22
forum: Programming Talk
---

### Post by nismoskys on 2006-03-22
I didnt really know where i should post this, so i put it here..

i was just wondering, is there any way to perform an action with bbips using a single line? Rather than going   

bbips
2
4
1024
768

Is there any way to perform that whole action in a single line, instead of having to push enter after each option?

thanks.

---

### Post by IYY on 2006-03-22
If you just want to repeat pre-coded instructions you could make a text file, call it instructions.txt and then run

cat instructions.txt | bbips

If you really just want to place the instructions in one line and run it interactively (I don't know why), you could do:

echo -e '1\n2\n3' | bbips

In this case, the commands bbips will get will be 1, 2 and 3.

---

### Post by nismoskys on 2006-03-23
cool.. thnx IYY it works, but the reason i need it to work is still not working..
i installed the "nautilus-scripts" thing where  you can execute a script on certain files by right clicking on them.

i pasted the command into a text file nd put it in the nautilus-scripts folder.. but it doesnt show up in the menu. i guess im not doing something right to make it an "executable file"..cuz all i did was put that command in a text file.

any suggestions would be welcome :)

---

### Post by IYY on 2006-03-23
First of all, any script file needs to start with the line **#!/bin/bash** (or #!/bin/sh or any other shell you wish to use). 

Second, it needs to be made executable (**chmod +x yourscript**).

---

### Post by nismoskys on 2006-03-23
cool thanks.

---

