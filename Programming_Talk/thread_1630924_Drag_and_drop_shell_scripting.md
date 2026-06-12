---
title: "Drag and drop shell scripting"
date: 2010-11-25
forum: Programming Talk
---

### Post by malkierian on 2010-11-25
OK, so, for a while I was using andLinux to run a program that was only possible under Linux, and I had a Windows batch file that ran the andLinux terminal feeding it a .sh as one argument that had the following contents in it:

```
#!/bin/bash

scriptPath=${0%/*}/;

filePath=~/windows$1;
fileTitle=$2;
fileExt=$3;

if [ "$fileExt" = "brlyt" ]; then
    ${scriptPath}benzin r "${filePath}${fileTitle}.brlyt" "${filePath}${fileTitle}.xmlyt"
elif [ "$fileExt" = "brlan" ]; then
    ${scriptPath}benzin r "${filePath}${fileTitle}.brlan" "${filePath}${fileTitle}.xmlan"
elif [ "$fileExt" = "xmlyt" ]; then
    ${scriptPath}benzin m "${filePath}${fileTitle}.xmlyt" "${filePath}${fileTitle}.brlyt"
elif [ "$fileExt" = "xmlan" ]; then
    ${scriptPath}benzin m "${filePath}${fileTitle}.xmlan" "${filePath}${fileTitle}.brlan"
else exit
fi
```I would drag and drop a file onto the batch file, which would then take the file argument, separate it into path, filename, and extension parts, and feed them to the andLinux terminal as arguments along with shell script, as such:
```

@echo off
:start

set x=%~p1

set linuxPath=%x:\=/%
set fileName=%~n1
set fileExt=%~x1
set fileExt=%fileExt:.=%

"C:\Program Files\andLinux\Launcher\andCmd.exe" ~/windows/sources/benzin/dnd.sh "%linuxPath%" "%fileName%" "%fileExt%"


:end
```
For example, I would take a file, whose filepath argument is "C:\sources\benzin\test.txt", and the batch file would feed the following arguments:
linuxPath = /sources/benzin/
fileName = test
fileExt = txt

Now, I set this up this way because I found out before that it's a lot more complicated to pull those variables out of a file argument in Linux Bash than it is in Windows Batch.

My question is, how would I switch the parts of the batch file over to shell scripting so I can drag and drop on top of the shell script.

Speaking of, whenever I try to drag and drop on the .sh file, I get "Error copying to xxx.sh: the destination is not a folder".  How would I go about making something I can drag and drop files onto to run the script in terminal with the filepath argument?

P.S.  I am running 10.10.

---

### Post by bodhi.zazen on 2010-11-25
I can not tell from your posts exactly what you are wanting to do 

I suggest you see:

[http://linuxcommand.org/](http://linuxcommand.org/)

Once you learn the basics, bash scripting should be easy.

---

### Post by malkierian on 2010-11-25
Alright, then, let's start with one thing at a time:

First, these functions, in Windows Batch, can pull apart a filepath into pre-path, filename and extension.  For example, I give this batch file:

```
@echo off
:start

set x=%~p1
set newline=^& echo.

set linuxPath=%x:\=/% **(removes leading "C:", and switches all back slashes to forward slashes)**
set fileName=%~n1 **(name of file, without path and without extension)**
set fileExt=%~x1 **(extension, including period)**
set fileExt=%fileExt:.=% **(removes leading period from the last funciton)**

echo **%linuxPath%**%newline%**%fileName%**%newline%**%fileExt%**

:end
```a command-line argument (i.e. drag and drop) of "C:\sources\test.txt".  It would then output something like this:

```
/sources/ **(linuxPath)**
test **(fileName)**
txt **(fileExt)**
```

How do I do that in Bash?

(By the way, it doesn't matter how complicated it is anymore, I'm running a virtual machine.  I just had to do this before because it was so complicated that no one wanted to help me out.  I had to do it in Batch [Windows], which was what I already knew)

---

### Post by malkierian on 2010-11-26
Bump...

Plus, I was wondering if a mod could possibly move this to the "Development and Programming" forum?  I didn't realize it was there, and I know that this would be a better topic for such a forum.  (I ask this because I don't want to cross-post)

EDIT:  Nevermind, I decided to do it in Python instead, and it took me about 45 minutes to get the program working.

---

