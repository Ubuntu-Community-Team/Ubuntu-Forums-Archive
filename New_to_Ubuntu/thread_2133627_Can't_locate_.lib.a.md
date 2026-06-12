---
title: "Can't locate ./lib/*.a"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by kapi on 2013-04-08
I'm trying to install ARToolkit and can't seem to get past this one section in the instructions. I'm supposed to use the following command.
sudo cp ./lib/*.a /usr/local/lib/

However I keep getting cannot find file, which is understandable.

Has anyone any idea how I should proceed?

I'm following instructions from the following web site. [http://tech.enekochan.com/2012/05/01/install-artoolkit-2-72-1-in-ubuntu-10-10/](http://tech.enekochan.com/2012/05/01/install-artoolkit-2-72-1-in-ubuntu-10-10/)

Thanks

---

### Post by kuifje09 on 2013-04-08
Did you see them yourself, in the directory where you are...
The files should exist if compilation went okay.

When you execute a sudo your current dir may have changed.( Not true, just tested )

just as a suggestion, I am not familiar with ARTool.

Update :  sudo does not change the current directory

---

### Post by Bashing-om on 2013-04-08
kapi; Hi !

In addition to          kuifje09's post; in the command "sudo cp ./lib/*.a"--- the ",/" in "./lib/" says in effect - in this directory -; is your present working directory "that" directory that contains the file to be copied ?[INDENT=3]
just try'n to help

[/INDENT]

---

### Post by kapi on 2013-04-09
> **Bashing-om said:**
> kapi; Hi !

In addition to          kuifje09's post; in the command "sudo cp ./lib/*.a"--- the ",/" in "./lib/" says in effect - in this directory -; is your present working directory "that" directory that contains the file to be copied ?[INDENT=3]
just try'n to help

[/INDENT]

Hi, thanks for the replies. I understand the file structure and navigation it's just that when I checked the lib folder in the current directory there didn't appear to be any files with .a as an extension.

Maybe I'll just start again eh.

Thanks again

---

### Post by steeldriver on 2013-04-09
If a source distribution involves a local lib directory, that usually means that part of the build process is to create its own .a and/or .so library files - so what was the result of the ./configure and make commands? did they complete successfully or were there errors? if errors occurred then maybe the .a file(s) that you are trying to copy didn't get created

---

### Post by kapi on 2013-04-09
> **steeldriver said:**
> If a source distribution involves a local lib directory, that usually means that part of the build process is to create its own .a and/or .so library files - so what was the result of the ./configure and make commands? did they complete successfully or were there errors? if errors occurred then maybe the .a file(s) that you are trying to copy didn't get created

Thanks, you may be right. I'll need to check later as I'm not at my laptop. 

Thanks

---

