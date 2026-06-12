---
title: "c++ compiler?"
date: 2005-06-16
forum: Programming Talk
---

### Post by karmah on 2005-06-16
I used to program c++ when i had windows. Now I want to do it in Ubuntu too but I can't..I've failed installing devcpp for linux and i can't use 'gcc <file.cpp>' to compile...
I'm a linux-noob so you might have to gimme a little step-by-step walkthrough :)
as usual: thx in advance anyone.

---

### Post by thumper on 2005-06-16
gcc is a C compiler.  To compile C++ you need to use g++.

My 3.4.1 install of gcc installed /usr/bin/g++-3.4 which I sym-linked to g++ so normal build scripts / makefiles found it automatically.

---

### Post by karmah on 2005-06-16
Thx, so ok..hmm..i compiled it i think...where did the program end up then? it's not in the same folder

---

### Post by stubby on 2005-06-16
[QUOTE=karmah]Thx, so ok..hmm..i compiled it i think...where did the program end up then? it's not in the same folder[/QUOTE]
 Sure? If i remember right normally it's called something like a.out

If you want to name the file it outputs to, just add a -o flag 
eg.
g++ -o myoutput myfile.cpp

---

### Post by karmah on 2005-06-16
YAY! Thank you very much, dewd!

---

### Post by leohart on 2005-07-01
[QUOTE=thumper]gcc is a C compiler.  To compile C++ you need to use g++.

My 3.4.1 install of gcc installed /usr/bin/g++-3.4 which I sym-linked to g++ so normal build scripts / makefiles found it automatically.[/QUOTE]

Thanks thumper, you saved me big time. Was trying to figure out why gcc doesn't work with my C++ Helloworld.

However, I like the a little IDE. I looked around and saw KDevelop. I got it through Synaptic. And now when I start a new project I chose HelloWorld project in KDevelop new project wizard.

Whoa, they gave me the code and the comments and everything. Looks awesome. I go Build -> Compile Project and WHAM :-> Error ?

I don't get it :(

---

### Post by thumper on 2005-07-02
[QUOTE=leohart]Thanks thumper, you saved me big time. Was trying to figure out why gcc doesn't work with my C++ Helloworld.

However, I like the a little IDE. I looked around and saw KDevelop. I got it through Synaptic. And now when I start a new project I chose HelloWorld project in KDevelop new project wizard.

Whoa, they gave me the code and the comments and everything. Looks awesome. I go Build -> Compile Project and WHAM :-> Error ?

I don't get it :([/QUOTE]
OK.  What is the error then?

---

### Post by poskok on 2005-07-08
Thak you boys, for this site!

---

