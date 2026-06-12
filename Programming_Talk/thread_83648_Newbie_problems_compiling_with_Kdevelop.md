---
title: "Newbie problems compiling with Kdevelop"
date: 2005-10-29
forum: Programming Talk
---

### Post by blastradius on 2005-10-29
When trying to compile a C++ program using Kdevelop i get the following error:-

checking for working makeinfo... missing
checking for C++ compiler default output file name... 
configure: error: C++ compiler cannot create executables
See `config.log' for more details.
*** Exited with status: 77 ***

I have no such problems with Anjuta but would prefer to use Kdevelop.  I've noticed that Kdevelop compiles with the C++ compiler whereas Anjuta refers to the compiler as g++, is this the problem and how can i change the setting in Kdevelop.

Thanks

Eric

---

### Post by toojays on 2005-10-29
Have you install build-essential?

---

### Post by ofek on 2005-10-29
Try writing the next command in terminal: "sudo apt-get install build-essential".

---

### Post by blastradius on 2005-10-30
yes i've already installed it.  As i said Anjuta works fine.

Can't understand it myself.  I'll try re-installing build-essential.

Ok didn't make any difference, the build-essential i have installed is the newest version.

Any ideas?

---

### Post by toojays on 2005-10-30
Post what it says in configure.log about the error. Recently someone in these forums had a problem which was caused by KDevelop trying to cross-compile an application for Windows.

---

### Post by blastradius on 2005-10-30
Ok, i could be being stupid here but how do i access the config.log?
As i said, i'm just getting started programming so i've a lot to learn.

Thanks for your reply.

---

### Post by toojays on 2005-10-30
I'm not sure where kdevelop puts it. Look in the directory where the rest of your source code is.

This is an example of why it's not such a good idea to learn programming with an IDE . . . it hides too much information from you.

---

