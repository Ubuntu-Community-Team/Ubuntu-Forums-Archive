---
title: "KDevelop Permission denied, error 126"
date: 2008-04-10
forum: Programming Talk
---

### Post by maigibs on 2008-04-10
hi,
this is my first post in your forum.
I've just started to programming c++ with g++ using ubuntu 7.10 (just installed, true greenhorn to ubuntu).

First, I created hello-world program 

#include <cstdio> 
int main() { printf("Hello World\n"); return 0;}

with gedit, compiling and linking it with g++ -o hello hello.cpp,
finally running it with ./hello works fine and shows "Hello World" in console window. 

Now I tried to repeat this task in KDevelop 3.5.8. But serious error occured:

/home/dev/hello: Permission denied
*** Exited with status: 126 ***  

Does KDevelop need special permissions on folder /xyz/hello? On the other hand, using gedit and g++ writing files to same folder and executing ./hello works correctly.

There is also just another problem: when clicking Help and KDevelop Handbook an error message appears: Could not launch Help Center ... Could not find service 'khelpcenter'. 

Can anybody help me to solve these both problems? I really appreciate any help of you.

Best regards, cliff

I should note that I installed the complete KDevelop system on gnome-based Ubuntu 7.10 also including some KDevelop docs. Also, I have tried to check /etc/fstab whether exec option is omitted, but /etc seems to be empty, no files were listed (insufficient privileges?)

---

