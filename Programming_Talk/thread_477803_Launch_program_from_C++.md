---
title: "Launch program from C++"
date: 2007-06-18
forum: Programming Talk
---

### Post by Kimm on 2007-06-18
Is there any way to launch a program in C++ without using "system()"?

My application is in Qt4 and I find that the app freezes if I use that function. I would like the app to be responsive, but still wait for the other program to close.

If possible, I would like to continuously read the output of the other program (to show progress in a progressbar for example).

Any help is appretiated! :D

---

### Post by nitro_n2o on 2007-06-18
In this case you need to fork() then use execvp("program_name") to run the program

---

### Post by nitro_n2o on 2007-06-18
```
if (!fork()) {
   // code in parent your original program 
} else {
  execvp("ls", NULL); 
}
```

Will that help? It'll be interesting to see other way too..

---

### Post by Kimm on 2007-06-18
> **nitro_n2o said:**
> In this case you need to fork() then use execvp("program_name") to run the program

Oh! Forgot to add... It needs to work on both Linux and Windows :/
I would prefer to use the same function on both... but if I have to, I'll specify different functions for Windows and Linux.

---

### Post by maddog39 on 2007-06-18
I dont think thats very possible unless you either implement a platform independent layer, or you use another library to handle that for you. Perhaps using SDL_threads or something and run system() in another thread so its running along side of the application.

---

### Post by Kimm on 2007-06-19
> **maddog39 said:**
> I dont think thats very possible unless you either implement a platform independent layer, or you use another library to handle that for you. Perhaps using SDL_threads or something and run system() in another thread so its running along side of the application.

If there is a way to do this in Windows (read the output and everything, not using fork() and execvp()) I could write headers for Windows and Linux specifying different functions (with the same name) for both systems.

Is there a way to do it in windows?

---

### Post by harun on 2007-06-19
Are you going to be building your application on Windows with gcc (g++) or Microsoft's compiler?

---

### Post by Kimm on 2007-06-19
> **harun said:**
> Are you going to be building your application on Windows with gcc (g++) or Microsoft's compiler?

I'll be building it with G++. Though I plan to (if I manage) compile it in Linux (using mingw)

---

### Post by vexorian on 2007-06-19
I guess you meant windows.

You can use winapi from a mingw32 compiled project just as fine, so you can just have some #ifdef conditions to use that winapi call to launch a program. (Use MSDN for info about how to use winapi...)

---

### Post by Kimm on 2007-06-19
> **vexorian said:**
> I guess you meant windows.

You can use winapi from a mingw32 compiled project just as fine, so you can just have some #ifdef conditions to use that winapi call to launch a program. (Use MSDN for info about how to use winapi...)

No, I really meant Linux. I plan on crosscompiling, unless I find someone with a Windows computer willing to set up a build environment...
I'll look into WinAPI

---

### Post by vexorian on 2007-06-19
as nice as cross compiling is, you still need to test it in windows... Even if it compiled correctly how would you know it actually works? For these kind of things dual boot is good (bad news I guess).

---

### Post by Kimm on 2007-06-19
> **vexorian said:**
> as nice as cross compiling is, you still need to test it in windows... Even if it compiled correctly how would you know it actually works? For these kind of things dual boot is good (bad news I guess).

I have a friend willing to play "beta tester" :P

---

### Post by Kimm on 2007-06-20
I think I have an idea that would work on all platforms!

If I write a program (lets call it 'dummy') that is executed by the first program (using system("./dummy <args> &");) then the first program should lock up. The first program can then wait for 'dummy' to write a specific file (signaling that the process has ended).

Only problem is this:

I doubt that in a windows terminal:

<command> **&**

works in the same way as it does in Linux... anyone know of anything equailent?

---

### Post by kknd on 2007-06-20
use some compiler macros to target different os (#ifdef tag and, etc).

---

### Post by bboozzoo on 2007-06-20
in Qt 3.4 there used to be QProcess class designed for this kind of tasks, it's quite probable that same facility is present in 4.x, you might give it a try instead of wasting time on your own solution since someone has already done it :)

---

### Post by Kimm on 2007-06-20
> **bboozzoo said:**
> in Qt 3.4 there used to be QProcess class designed for this kind of tasks, it's quite probable that same facility is present in 4.x, you might give it a try instead of wasting time on your own solution since someone has already done it :)

THANK YOU!! I always thought Qt4 should have something like this, but I was unable to find it. This looks exactly like what I would need!

---

