---
title: "C++, Gedit, and External Tools"
date: 2009-08-04
forum: Programming Talk
---

### Post by Optimus_Jazz on 2009-08-04
Basically what I want to do is compile and run my c++ code from gedit.
I've been having this problem for months,and a friend had configured his to do it,even when I copied this method it did not work(some months ago) so I just switched to windows for programming,but this is not an option any more.

My college lecturer gave us the following

C/C++ Compile 

```


#!/bin/bash
# Store the file name in a variable
echo "Compiling " $GEDIT_CURRENT_DOCUMENT_PATH
FILE_NAME=$GEDIT_CURRENT_DOCUMENT_NAME
# Check if file extension is .cpp
if [ `echo $FILE_NAME | cut -d "." -f 2` = "cpp" ]
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 4`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
g++ -o $FILE_NAME_BASE $GEDIT_CURRENT_DOCUMENT_NAME
fi
# Check if the file extension is c
if [ `echo $FILE_NAME | cut -d "." -f 2` = "c" ]
then
FILE_NAME_LEN=`expr ${#FILE_NAME} - 2`
FILE_NAME_BASE=${FILE_NAME:0:$FILE_NAME_LEN}
gcc -o $FILE_NAME_BASE $GEDIT_CURRENT_DOCUMENT_NAME
fi
exit 0


```


Running

```

cat > runit.sh << datatag
#!/bin/bash
${GEDIT_CURRENT_DOCUMENT_NAME%.*}
read -p"Program finished. Press any key to exit..." -n1
datatag
chmod u+x runit.sh
gnome-terminal --command="runit.sh" --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR --title="${GEDIT_CURRENT_DOCUMENT_NAME%.*}" 


```

Using external tools,from what i understand, i had to use a shortcut key such as F1,F2 etc and then paste the code into the box,but this doesn't work.Can anyone shed some light onto the situation,thanks!

---

### Post by Optimus_Jazz on 2009-08-04
I have got the compile command working,it turns out g++ wasn't installed,but when i try to run the program in the terminal it gives me the error :

"there was an error creating the child process for this terminal"

as i recall this is the exact same problem i had the last time.

---

### Post by Optimus_Jazz on 2009-08-04
Reading up on a friends post who had the same problem it turns out that 


PATH=.:$PATH

needs to be added to fix the path to the ect/profile

Unfortunatley he is on holidays so i cannot ask him were in the code it needs to be added to,anyone have any ideas?Its this code :

```
cat > runit.sh << datatag
#!/bin/bash
${GEDIT_CURRENT_DOCUMENT_NAME%.*}
read -p"Program finished. Press any key to exit..." -n1
datatag
chmod u+x runit.sh
gnome-terminal --command="runit.sh" --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR --title="${GEDIT_CURRENT_DOCUMENT_NAME%.*}"
```

---

### Post by dwhitney67 on 2009-08-04
I would suggest that you fix the following statement within gedit:
```

gnome-terminal --command="runit.sh" --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR --

```
to be:
```

gnome-terminal --command="./runit.sh" --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR --

```
Note the "./" before the runit.sh.

---

### Post by Optimus_Jazz on 2009-08-04
Thanks for the help,with your help the terminal is now opening but it gives me the following message :

```

./runit.sh: line 2: myprogram: command not found
Program finished. Press any key to exit...

```

---

### Post by dwhitney67 on 2009-08-04
Did you compile your program successfully?  All that message is telling you is that the executable "myprogram" is not found.

Try this program to see if it works for you:
```

#include <iostream>

int main() { std::cout << "hello" << std::endl; }

```

---

### Post by Optimus_Jazz on 2009-08-04
Im just assuming its compiled as it says done when I use the accelerator key with the code for compiling.

Usin your code it gives me the same message again.

---

### Post by dwhitney67 on 2009-08-04
Personally, I use the **Tools->Compile** and **Tools->Run Application** menu choices.

When you compile the program, you should see something like the following in the Shell Output of Gedit:
```

Running tool: Compile

Compiling  /home/dwhitney/myprogram.cpp

Done.

```

---

### Post by Optimus_Jazz on 2009-08-04
I know but seeing as how my lecturer wrote the compile code theres not much i can do,all i know is that when he compiles it doesn't give us a message saying that its done so.
Also,i dont have that option on my tools.

Using Ubuntu and writing code,could you say that gedit is better for writing,compiling and running code or are there alternatives?

---

### Post by dwhitney67 on 2009-08-04
> **Optimus_Jazz said:**
> I know but seeing as how my lecturer wrote the compile code theres not much i can do,all i know is that when he compiles it doesn't give us a message saying that its done so.
Also,i dont have that option on my tools.

I was running Gedit under Ubuntu 9.04.  Surely when you run Gedit you have a "Tools" pull-down menu?  Within that menu, half way down, is the "Compile" option.  A little bit further down, is the "Run Application" option.

> **Optimus_Jazz said:**
> 
Using Ubuntu and writing code,could you say that gedit is better for writing,compiling and running code or are there alternatives?

I'm probably the last person on Earth you should ask this question to.  Personally I hate IDEs of any flavor, and instead I use the command line and vim.  For complex applications I create my own Makefile.

---

### Post by Optimus_Jazz on 2009-08-04
Ah,you know what i think i did,but i overwrote them!

Never mind,i am just going to use the command line in terminal to run and compile the code.

Thanks for all the help!:D

---

### Post by harry2006 on 2009-08-04
the best bet to get rid of such issues would be to use a commandline editor ...i like doing all my programming stuss in vi only...though you can try emacs as well...

---

### Post by paulobrasil on 2011-02-20
The corret code :D ::

```
cat > runit.sh << datatag
#!/bin/bash
${GEDIT_CURRENT_DOCUMENT_PATH%.*}
read -p"Program finished. Press any key to exit..."  -n1
datatag
chmod u+x runit.sh
gnome-terminal --command="./runit.sh" --working-directory=$GEDIT_CURRENT_DOCUMENT_DIR --title="${GEDIT_CURRENT_DOCUMENT_NAME%.*}"

```

---

