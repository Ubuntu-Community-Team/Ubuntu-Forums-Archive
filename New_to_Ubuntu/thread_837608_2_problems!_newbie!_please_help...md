---
title: "2 problems! newbie! please help.."
date: 2008-06-22
forum: New to Ubuntu
---

### Post by sh7436 on 2008-06-22
Hi everyone,

I have just installed ubuntu and im loving it, but im having some problems. 
1) when i compile a c program, ( the hello world to be exact)

gcc hello.c -o hello

it compiles (i think) and theni type hello but nothing happens and it says bash: cannot find hello. But surely typing hellp should cause it to say hello world on screen.

2) when i type sudo apt-get instal build essential i get the following: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build

and i have updated build-essential and build but still no joy.

anyone know? TIA!

Simon

---

### Post by Xerp on 2008-06-22
1. Try ./hello

2. Apt is telling you there isn't a package called "build"

---

### Post by UltraMathMan on 2008-06-22
Try ```
sudo apt-get install **build-essential**
```.

---

### Post by the_doc on 2008-06-22
If it compiles you would need to run it as ./hello, as suggested by Xerp.

---

### Post by sh7436 on 2008-06-22
hehe silly me with the typos! seems i cant read from a website lol thanks alot! its downloading the update now :D 

Also the ./ has worked in the compiling, so thank you for the extremely fast reply. just one final question. At uni i can just type the name of the bit after the -o... howcome i need the ./ here and what does it represent

Many thanks again

Simon

---

### Post by Barrucadu on 2008-06-22
Are you using Linux at uni? The ./ signifies the current directory. Without it, the shell looks for a program called 'hello' in your $PATH.

---

### Post by the_doc on 2008-06-22
./ represents the current directory.  If the directory where the binary is located was on your path then you wouldn't need it.

---

### Post by nhandler on 2008-06-22
> **sh7436 said:**
> hehe silly me with the typos! seems i cant read from a website lol thanks alot! its downloading the update now :D 

Also the ./ has worked in the compiling, so thank you for the extremely fast reply. just one final question. At uni i can just type the name of the bit after the -o... howcome i need the ./ here and what does it represent

Many thanks again

Simon

"." actually represents the current directory. ".." represents the parent directory. "./hello" tells the computer to run the script "hello", which is located in the current directory. You are using the scripts "relative path" to run it. You can also run the script using its "absolute path". To do this, run "/home/yourName/hello". That command assumes that the hello file is located in your home directory. You also would have to replace "yourName" with your username.

---

### Post by nick_h on 2008-06-22
> Without it, the shell looks for a program called 'hello' in your $PATH.
Yes.  Create a directory called bin under your home directory and it will be put in your PATH.

---

