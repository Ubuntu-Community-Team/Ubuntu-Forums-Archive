---
title: "Compiler for cobol + vim or vi ??"
date: 2010-02-10
forum: Programming Talk
---

### Post by itrehalf on 2010-02-10
Greetings Im new here in the forum, and i have a problem with VIM. 
As you would notice its my first time programming with VIM (i used to program in other languages like java, C , c++ ) anyhow my problem is that i dont know how to set the compiler in the text editor called VIM.
And also i dont know wich compiler should i use, just tell me a good one that works fine with VIM.

If i am missing somth or sort of , just let me know , It is a must use VIM for me  (due to work reasons).

Conclusion: So my problem basicaly is how to set the compiler to the text editor and wich compiler should i use.
BTW i read the tutorial i think the name is : "How to start programming" but there isnt a tutorial for cobol so if i am successful i'll make one guide.

Thank you for your time,


Itre.

---

### Post by bogdan.veringioiu on 2010-02-11
Hi.
Using vim as a code editor is implying a little change in your approaching of coding/compiling.
I suggest 2 things:
-use one terminal with vim for editing your files, and use another terminal for compilation. (or use Terminator which will allow you to split terminal screens)
-within the vim editor, type:
> :!command
This way, you execute a command without leaving vim (the command can be your compilation command)
Bogdan

---

### Post by wmcbrine on 2010-02-11
COBOL is a pretty neglected language for Linux, but OpenCOBOL is in the repos:

sudo apt-get install open-cobol

---

