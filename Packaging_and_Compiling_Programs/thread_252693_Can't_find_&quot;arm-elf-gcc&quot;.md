---
title: "Can't find &quot;arm-elf-gcc&quot;"
date: 2006-09-07
forum: Packaging and Compiling Programs
---

### Post by chochem on 2006-09-07
I feel like an idiot for asking this kind of question but I'm beginning to run out of ideas. 

I'm trying to compile Rockbox, the open source OS for a number of arhocs, iriver and apple DAPs, but I keep getting told that I do not have this 'arm-elf-gcc'. I've tried using the package manager to locate something like this but with no success. I've tried following a suggestion to install 'build essentials' or something like that with no success. I have a feeling I should learn the basiscs before venturing into this but if anybody can tell me how to get this thing, I promise I will at some future date :)

EDIT: Nevermind, found the answer I was looking for in the Rocbox forums.

---

### Post by shak541 on 2007-07-10
Hi, I am doing the same thing as you(compiling rockbox) and having the same issue. Could you please point me to where you found the solution?
,thanx

---

### Post by st14n on 2007-11-24
I guess you've found a solution, but for future reference:
[http://www.rockbox.org/twiki/bin/view/Main/CrossCompiler]("http://www.rockbox.org/twiki/bin/view/Main/CrossCompiler")

---

### Post by airtonix on 2008-01-11
I too am having a go at compiling latest rockbox...

keen to have vcard viewer active.

st14n is right. ([http://www.rockbox.org/twiki/bin/view/Main/CrossCompiler](http://www.rockbox.org/twiki/bin/view/Main/CrossCompiler))
descibes a file in the svn or build package that will get the proper compiler you require.

> [rockbox-build-package]/tools/rockboxdev.sh

you will also need build-essential prior to running the script. 

> sudo apt-get install build-essential

---

### Post by clonne4crw on 2009-07-10
+1. Building for Sansa Fuze.
I can comfirm that tools/rockboxdev.sh works, and I'm compiling arm-elf-gcc right now. Thanks!

---

