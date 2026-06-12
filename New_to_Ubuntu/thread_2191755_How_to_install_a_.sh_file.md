---
title: "How to install a .sh file"
date: 2013-12-04
forum: New to Ubuntu
---

### Post by 4dr14n on 2013-12-04
Hello all!

I have a lil roblem that I'd like to share with you, because I think, for a lot of you, it will be easy to solve, but I don't find on the net how to and I can't follow the handbooks for Ubuntu ;).

I want to install a program (Mesquite) and from the project's website I picked a .sh file but I don't know how to install it nor from the terminal nor from synaptic (or whatever other source) ...
The file's name is run_mesquite.sh, maybe it could be useful if you put the inputs here ;)


Thank you so much in advance!!

---

### Post by drmrgd on 2013-12-04
Generally speaking, you would just make the file executable and then execute it.  So, from the terminal, you could run these two commands, one after the other:

```

chmod +x run_mesquite.sh
./run_mesquite.sh

```

I had a quick look, and found installation instructions for a program that looks similar to what you describe:

[http://mesquiteproject.org/Mesquite_Folder/docs/mesquite/installation/installationUNIX.html](http://mesquiteproject.org/Mesquite_Folder/docs/mesquite/installation/installationUNIX.html)

If this is the same program, then this should help you get that package installed.

---

### Post by 4dr14n on 2013-12-04
First of all, thank you a lot!!
I wrote just ./run... and it worked but what made me confused (and the reason why I wrote this) is that when I wrote the first input ("[COLOR=#000000][FONT=Ubuntu Mono]chmod +x run_mesquite.sh) it appeared nothing... but, anyway it ran =).[/FONT][/COLOR]

---

### Post by heir4c on 2013-12-04
With the first command you make the file executable. 
With the second command you run the file.

---

### Post by oldos2er on 2013-12-04
Moved to Absolute Beginners.

---

### Post by JKyleOKC on 2013-12-04
> **4dr14n said:**
> First of all, thank you a lot!!
I wrote just ./run... and it worked but what made me confused (and the reason why I wrote this) is that when I wrote the first input ("[COLOR=#000000][FONT=Ubuntu Mono]chmod +x run_mesquite.sh) it appeared nothing... but, anyway it ran =).[/FONT][/COLOR]Nothing appearing after the first command is absolutely normal action. In most Linux distributions, including all of the *buntu varieties, successful operations don't bother to tell you they worked. Only if they failed will you see a message from them.

Another major difference from Windows is that commands only execute if found in the folders listed in the PATH environment variable. Windows also looks in the current folder, before searching the path, but Linux doesn't do this. The "./" at the front of the second command tells the system to look only in the current folder for the command. Without it, you would get a "Command not found" error message.

---

