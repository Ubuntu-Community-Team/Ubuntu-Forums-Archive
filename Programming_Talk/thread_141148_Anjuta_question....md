---
title: "Anjuta question..."
date: 2006-03-07
forum: Programming Talk
---

### Post by grim918 on 2006-03-07
I can't get seperate files to compile in Anjuta. Does anyone know how to work with that IDE. I'm new to linux. I created 3 files. An h file and two more files. when I compile them I get no errors but when I try to build I get an error saying that one two of the functions are undefined. I'm guessing that I have a linking problem. Can someone help me out and tell me the proper way to start a project in Anjuta and how to link all the files together. Thank you for any help.

---

### Post by Zdravko on 2006-03-08
grim918, I also have the same problem - a reason to uninstall it. It appears that when the files are in a single directory everything is ok. But Anjuta separates them into src and include. After that there is no way to compile a single programm. One possible (but also stupid) sollution is to provide the include directive the full path to the header file, like so:
> 
#include "/home/someuser/Projects/someproj/include/file.h"


---

### Post by grim918 on 2006-03-08
There has to be an easier way to link the files together with that IDE. Until I can figure it out I just went back to using g++ on the command line.

> g++ file.h file1.cc file2.cc  -o filename 

this links the files together and if you have no problems then it creates an executeable (filename).

---

### Post by Zdravko on 2006-03-08
grim918, that is the way I use now. It is safer and works exactly as I want.

---

### Post by Lord Illidan on 2006-03-08
How were you adding the files in Anjuta?
Project -> Add File should do the trick. It works for me.

---

### Post by Zdravko on 2006-03-08
Lord Illidan, did you try the separate compilation? Just include a header and then a cpp file. If it works, than it is strange :(

---

### Post by Lord Illidan on 2006-03-08
[quote=Zdravko]Lord Illidan, did you try the separate compilation? Just include a header and then a cpp file. If it works, than it is strange :([/quote]

Yep, I am using it for my own project with sdl and a header file and a .cc file seperate of the main file. They are in the same folder, and I used the Project -> Add Files to add them.

---

### Post by grim918 on 2006-03-08
How do you start the project with Anjuta. I tried to start an empty project and just add my files as I go along but when I start a new project it includes a bunch of files, I have no idea what to do with them. Is there a way to start an empty project with Anjuta. I'm sure there is I just haven't figured it out yet. I'm new to linux.

---

### Post by Lord Illidan on 2006-03-09
I just edited the main.cc file.

---

