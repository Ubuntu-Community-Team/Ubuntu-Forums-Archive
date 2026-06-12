---
title: "Sript to copy"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by PKJack on 2012-11-15
Hi,
I am new to Ubuntu and its terminal. Currently I am doing a simulation project and I have to work on two different folders lets say "Folder1" and "Folder2". Simulation in "Folder1" gives "code.bin" file and I have to copy this file to "Folder2" and run another simulation in that folder. It is waste of time to copy "code.bin" file every time to another folder. So i need to code a script that does that automatically for me such that I can immediately switch to "Folder2" from "Folder1" and start the simulation. So any suggestions friends?

Regards :)

---

### Post by Paqman on 2012-11-15
You could just write a script that runs the simulation, then copies the output to the second location before starting the second simulation there.

[Basic BASH scripting]("https://help.ubuntu.com/community/Beginners/BashScripting").

---

### Post by drmrgd on 2012-11-15
Does Folder2's name ever change, or is it always the same?

As a start, you could do something like this:

```
#!/bin/bash

sim2Dir=$1

if [ -d "../$sim2Dir" ]; then
        if [ -e "code.bin" ]; then
                cp "code.bin" "../$sim2Dir" && eval "../$sim2Dir/code.bin"
        else
                printf "The file 'code.bin' does not yet exist!"
                exit 1
        fi
else
        printf "There is no directory called: %s\n" $sim2Dir
fi
```

The script will check for "folder2" and if it exists, it will cp 'code.bin' to that folder and execute it (I used eval because I don't know what kind of script it is...you might want to change how it's executed there).  If folder2 does not exists, then you get an error and the program exits.  You could change that error section to make it create folder2 and so on.  

To use the script, you can make it executable:

```
chmod +x cp_run.sh
```

And then run it like this:

```
./cp_run.sh folder2
```

Folder2 should be the actual name of the folder where you want to copy and run the 'code.bin' script.

---

### Post by PKJack on 2012-11-15
Thank you, drmrgd. But I am sorry that i did not understand few things in the suggested script. Does sim2Dir means "Folder2" (Yes it is same everytime)? And does  ```
" .../$sim2Dir"
``` means that i have to give full path of "folder2".

---

### Post by PKJack on 2012-11-15
I tried giving my "folder2" name in place of "sim2Dir" and tried running the script. It displayed following message:
```
 ./cpy_script.sh: line 7: ..//code.bin: Permission denied 
```

---

### Post by drmrgd on 2012-11-15
> **PKJack said:**
> Thank you, drmrgd. But I am sorry that i did not understand few things in the suggested script. Does sim2Dir means "Folder2" (Yes it is same everytime)? And does  ```
" .../$sim2Dir"
``` means that i have to give full path of "folder2".

Since I wasn't sure if 'folder2' was always going to have the same name, I elected to pass it to the script as an argument.  Within the script, then I was passing that argument into the variable called $sim2Dir.  We can simplify things if the folder name is always exactly the same by just hard coding that folder name in the script.  The way I did it, though gives you a little more flexibility if the name does happen to change for one reason or another.  Here's the change for a hardcoded "Folder2" directory:

```
#!/bin/bash

if [ -d "../Folder2" ]; then
        if [ -e "code.bin" ]; then
                cp "code.bin" "../Folder2" && cat "../Folder2/code.bin"
        else
                printf "The file 'code.bin' does not yet exist!"
                exit 1
        fi
else
        printf "There is no directory called: 'Folder2'!\n" 
fi
```

In regard to the path question, I went based on the assumption that you would be running the script from Folder1 every time based on the conditions that you mentioned above.  Without knowing more about what you're doing and how you have your data stored, it's hard to know what the real path would be; I would prefer more rigid, full paths to be on the safe side, though.  You can tailor the paths to meet your needs.  Just change the lines that say "../Folder2" to match the path and the name of the folder as you wish.  Then (after making it executable of course), run it by typing:

```
./name_of_script.sh
```

---

### Post by PKJack on 2012-11-15
Solved! Thank you very much for the helpful suggestions :) It made my work lot easier! 

Regards

---

### Post by drmrgd on 2012-11-15
> **PKJack said:**
> Solved! Thank you very much for the helpful suggestions :) It made my work lot easier! 

Regards

Great!  Glad to help!

---

