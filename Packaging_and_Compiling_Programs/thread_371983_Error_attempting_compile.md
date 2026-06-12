---
title: "Error attempting compile"
date: 2007-02-27
forum: Packaging and Compiling Programs
---

### Post by humbll on 2007-02-27
I did the 
 sudo apt-get install build-essential

and also installed Scite editor as my programming environment but when i do a simple test prog and try to compile (in Scite) i get the error:

------------------------------------------------------------------------------------------------------------------------------------

4:20: error: studio.h: No such file or directory
helloworld2.c:14: warning: return type defaults to 'int'
helloworld2.c: In function 'main':
helloworld2.c:18: warning: implicit declaration of function 'printf'
helloworld2.c:18: warning: incompatible implicit declaration of built-in function 'printf'
helloworld2.c:21:15: warning: no newline at end of file

-----------------------------------------------------------------------------------------------------------------------------------
A search of my drive reveals no studio.h file on the system. Can someone please explain this?
And why aren't these packages available by default on a unix?
I am using Edgy Eft 6.10
Thanks.

---

### Post by bchaffin72 on 2007-03-12
I also had this trouble. Perhaps the default Ubuntu install does not fully install gcc. Because I also use c++, I used the Synaptic Package Manager to install g++, which updated and placed everything properly. Gcc now works as it should.

---

