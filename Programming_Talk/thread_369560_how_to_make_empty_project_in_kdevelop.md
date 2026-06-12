---
title: "how to make empty project in kdevelop?"
date: 2007-02-24
forum: Programming Talk
---

### Post by thegrimgod on 2007-02-24
Can somebody tell me how to make a true empty c++ project in kdevelop, im tryin the simple hello program , but i have no choice to select the empty project ,or i dont know how, i go through the name..folder..of the project ,then i get author , some version control, have no clue what that is and some templates for my .h and .cpp files, but nothin else
ty for any help that u can give me

---

### Post by barney_1 on 2007-02-24
I had the same issues when I started looking at C++ yesterday.  Until you get an answer, I'd suggest just using gedit (gnome) or kate (kde) to create your tutorial files.  Then compile those files:
```
g++ filename.cpp
```

---

### Post by thegrimgod on 2007-02-24
yea , i was doing that , but its gettin old fast to compile each file, im training for contest doing many problems , i liked the easy use of vc++ 2005 i think it was, u just compile the project and switch between cpps, in any case i know it is possible in kdevelop, i read something on their web page , but i cant understand/find what they sayin
waitin for an answer , but ty for interest

---

### Post by j_g on 2007-02-25
1) There is no Linux IDE comparable to the ease and power of Microsoft dev tools such as Visual C++.

2) If you happen to think that Linux dev tools are lacking, there are some Linux people who unfortunately will tell you that your complaints aren't justified, and things are just absolutely great if you forget all about your efficiency and productivity under Windows and just learn to like doing things "the old way" under Linux.

I wish I had a good answer for folks who, like me, recognize the deficiencies and inadequacies in Linux dev tools, but unfortunately, there is not a good answer. There is only the realization that you have to accept decreased productivity and efficiency, compared to Windows development, if you want to do Linux development. I know that it's a pain to issue a compiler/linker from the command line, or constantly be hand-editing some sort of "build/make" file when you want to change anything, but that's the state of Linux development circa 2007. And it's not entirely unexpected. Linux and its dev tools are free, and you get what you pay for. MS makes money from selling Windows, and it's the developers who made it all happen for MS, so MS treats them very well and makes sure that their job is as easy and quick as possible.

---

### Post by lnostdal on 2007-02-25
thegrimgod: 
if you (uhm, and i) can ignore the troll "j_g" i'd be more than willing to help you get started being actually efficient and productive under the Linux-environment with the help of a build-tool called Scons .. i can almost certainly guarantee that this will work out well if no one can help you with KDevelop specifically

i've tried to write something down here: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/) ..you can use another editor if Emacs scares you, but it is rather important that the editor can parse the output of GCC (most good programming-editors can do this)..  

if you have any preferences when it comes to editors i can make an addition to the writings that show how to set up something similar like this in that editor  .. (but KDevelop is way to klunky for me so i'm not going to try that .. not now at least:) .. and it seems GEdit cannot parse the output of GCC(?))

feel free to contact me on MSN/Jabber/IRC (less noise/trolling there)

---

### Post by harun on 2007-04-05
> **thegrimgod said:**
> Can somebody tell me how to make a true empty c++ project in kdevelop, im tryin the simple hello program , but i have no choice to select the empty project ,or i dont know how, i go through the name..folder..of the project ,then i get author , some version control, have no clue what that is and some templates for my .h and .cpp files, but nothin else
ty for any help that u can give me

[http://www.kdevelop.org/mediawiki/index.php/FAQ#How_to_create_a_truly_empty_project.3F](http://www.kdevelop.org/mediawiki/index.php/FAQ#How_to_create_a_truly_empty_project.3F)

---

