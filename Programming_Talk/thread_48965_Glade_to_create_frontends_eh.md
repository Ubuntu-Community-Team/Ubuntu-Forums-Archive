---
title: "Glade to create frontends eh?"
date: 2005-07-14
forum: Programming Talk
---

### Post by Haegin on 2005-07-14
So glade can create frontends which you can populate with code right? But is it possible to set glade to run commands when a certain button is clicked etc - effectively enabling a user to create frontends to a console program without much programming logic?
I am interested in creating a frontend for SoX to convert audio files between formats and wish to use glade to build the interface and then set it so the text fields and the drop down boxes are all variable which can be used in console commands run when the buttons are clicked. Is this possible?

---

### Post by tread on 2005-07-14
Glade will allow you to setup callbacks, which will show up as empty functions when you generate the code.  You just need to insert the code to exec sox or whatever then.
I got this sample code off a website:
```

#include <unistd.h>
#include <sys/wait.h>
#include <iostream>
using namespace std;

int main(){
   pid_t pid;
   int status, died;
   switch(pid=fork()){
   case -1: cout << "can't fork\n";
            exit(-1);
   case 0 : execl("/usr/bin/date","date",0); // this is the code the child runs 
   default: died= wait(&status); // this is the code the parent runs
   }
}

```

---

