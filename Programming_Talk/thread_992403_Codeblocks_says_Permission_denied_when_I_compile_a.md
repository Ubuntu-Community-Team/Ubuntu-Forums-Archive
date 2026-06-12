---
title: "Codeblocks says Permission denied when I compile and run my program"
date: 2008-11-24
forum: Programming Talk
---

### Post by arya6000 on 2008-11-24
Hi


I installed Codeblocks from apt-get and I wrote a simple hello world program to test it. When I run my program a new terminal opens and says:

> sh: /home/david/addressoffile: Permission denied 


Press Enter to continue.

Any idea why I keep getting it?

---

### Post by gpsmikey on 2008-11-24
I presume "addressoffile" is your executable you are creating?  does it have execute permission bit set?  (ls -l will show the permissions).  If "addressoffile" is a shell script that you have created, then it probably does not have the execute bit set - if it is the executable from the compiler, I thought it was generally set.  Does the directory have the permissions set right (I don't remember right off hand just what it needs).  Hopefully that will get you started until someone with just a *bit* more experience than me shows up :)

mikey

---

### Post by piettro14 on 2010-05-01
just save the new file with this format name.cpp then it will run :)

---

### Post by sheldon1 on 2010-11-29
I recently installed the newest version of Ubuntu (10.10) and installed Code::Blocks through the package manager. My old .cbp files open but, when run, give me the same error message. Oddly, this error only happens when there is a main.cpp, a filename.cpp, and a filename.h in one project. I opened an old project containing only a main.cpp file, and it runs fine.

The quick fix for me was to create a new project and copy and paste the code from my old projects into the new one.

---

### Post by hdy117 on 2011-05-26
I met the same problem,but when I create project in my host dir,it's OK.

---

