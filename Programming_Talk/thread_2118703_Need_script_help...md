---
title: "Need script help.."
date: 2013-02-22
forum: Programming Talk
---

### Post by Baldrick_NZ on 2013-02-22
Hi all,

I have a proprietary app that I use for my job, that I have managed to work well under Wine. 

However, there is a stand alone .bat file which, when activated, deletes certain files within the "Program Files" folder. Unsurprisingly, this .bat file won't execute under Wine.

So, what I need is a simple script which will replicate the situation for Linux.

Any script ideas would be gratefully received.

---

### Post by fdrake on 2013-02-22
> **Baldrick_NZ said:**
> Hi all,

I have a proprietary app that I use for my job, that I have managed to work well under Wine. 

However, there is a stand alone .bat file which, when activated, deletes certain files within the "Program Files" folder. Unsurprisingly, this .bat file won't execute under Wine.

So, what I need is a simple script which will replicate the situation for Linux.

Any script ideas would be gratefully received.

 run the bat file from the command line directly.Wine has already a command line emulator :
in termianl type:
```

user@Ubuntu:~$wine cmd
Z:\home\user>cd Desktop
Z:\home\user\Desktop>my_script.bat
Z:\home\user\Desktop>exit
user@Ubuntu:~$

```

i would check the code of the bat file in case uses directorie /pathc not present in winr. You may have to do some txt editing to adapt the script to your wine's dir system.

---

### Post by guyr34 on 2013-02-22
Use a newer winehq. There has been significant progress with newer versions in this area (> 1.5.20)

---

### Post by Baldrick_NZ on 2013-02-22
> **guyr34 said:**
> Use a newer winehq. There has been significant progress with newer versions in this area (> 1.5.20)

Thanks, but I find the dev version is too unstable to use for work purposes. I'll upgrade when it comes to the next stable version.

---

### Post by Baldrick_NZ on 2013-02-22
> **fdrake said:**
> run the bat file from the command line directly.Wine has already a command line emulator :
in termianl type:
```

user@Ubuntu:~$wine cmd
Z:\home\user>cd Desktop
Z:\home\user\Desktop>my_script.bat
Z:\home\user\Desktop>exit
user@Ubuntu:~$

```

i would check the code of the bat file in case uses directorie /pathc not present in winr. You may have to do some txt editing to adapt the script to your wine's dir system.

Tried that but wine went into debug mode. Odd. Thanks for your help though.

I'm really looking for the ability to click on a linux-based icon (script) which will then automatically delete the predetermined files. In much the same way as the .bat file does under Windows.

---

### Post by prodigy_ on 2013-02-22
You could rewrite the script in bash.

---

### Post by albandy on 2013-02-22
Or use DosBox:
dosbox -c command

for example
dosbox -c dir

---

### Post by Baldrick_NZ on 2013-02-22
> **prodigy_ said:**
> You could rewrite the script in bash.

This sounds like me, though I've not done it before. Any help would be much appreciated.

---

### Post by Vaphell on 2013-02-22
deleting files is not rocket science
rm <file>
eg

```
#!/bin/bash

#delete stuff
rm "$HOME/.wine/drive_c/Program Files/MyProgram/file1.txt"
rm "$HOME/.wine/drive_c/Program Files/MyProgram/file2.txt"
rm "$HOME/.wine/drive_c/Program Files/MyProgram/junk/file3.txt"

#run program
wine "$HOME/.wine/drive_c/Program Files/MyProgram/program.exe"

```

```
chmod +x launcher.sh #this makes the script executable
./launcher.sh 
```

---

### Post by Baldrick_NZ on 2013-02-23
> **Vaphell said:**
> deleting files is not rocket science
rm <file>
eg

```
#!/bin/bash

#delete stuff
rm "$HOME/.wine/drive_c/Program Files/MyProgram/file1.txt"
rm "$HOME/.wine/drive_c/Program Files/MyProgram/file2.txt"
rm "$HOME/.wine/drive_c/Program Files/MyProgram/junk/file3.txt"

#run program
wine "$HOME/.wine/drive_c/Program Files/MyProgram/program.exe"

```

```
chmod +x launcher.sh #this makes the script executable
./launcher.sh 
```

Thanks for this.

So to wrap this all up into a launchable script, I'd open gedit, copy n paste the detail in the top box into gedit and make the appropriate changes and save it as a dosbatch file? How would I apply the code in the 2nd box?

Sorry, I'm very new to programming and would be very appreciative of the input.

---

### Post by fdrake on 2013-02-23
> **Baldrick_NZ said:**
> Thanks for this.

So to wrap this all up into a launchable script, I'd open gedit, copy n paste the detail in the top box into gedit and make the appropriate changes and save it as a dosbatch file? How would I apply the code in the 2nd box?

Sorry, I'm very new to programming and would be very appreciative of the input.

open the terminal and type:
```
gedit ~/Desktop/launcher.sh
```
<copy/ paste code #1 /save (ctrl+s)>
<close gedit>
in the terminal type:
```

chmod +x ~/Desktop/launcher.sh

```
<to run the program type:>
```

~/Desktop/launcher.sh

```

---

### Post by Baldrick_NZ on 2013-02-23
> **fdrake said:**
> open the terminal and type:
```
gedit ~/Desktop/launcher.sh
```
<copy/ paste code #1 /save (ctrl+s)>
<close gedit>
in the terminal type:
```

chmod +x ~/Desktop/launcher.sh

```
<to run the program type:>
```

~/Desktop/launcher.sh

```

Awesome, thanks!

Now how would I go about executing 'launcher.sh' by double clicking on the icon?

---

### Post by fdrake on 2013-02-23
double click> select "run in terminal"

---

### Post by Baldrick_NZ on 2013-02-23
I found a way using Alacarte.

Thanks everyone for your help!!

---

### Post by fdrake on 2013-02-23
> **Baldrick_NZ said:**
> I found a way using Alacarte.
!
ehh? you mean the gnome menu editor?
[http://en.wikipedia.org/wiki/Alacarte](http://en.wikipedia.org/wiki/Alacarte)

---

### Post by Baldrick_NZ on 2013-02-25
> **fdrake said:**
> ehh? you mean the gnome menu editor?
[http://en.wikipedia.org/wiki/Alacarte](http://en.wikipedia.org/wiki/Alacarte)

Yup, that's the one. Thanks again!

---

