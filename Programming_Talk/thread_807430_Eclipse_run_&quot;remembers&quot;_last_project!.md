---
title: "Eclipse run &quot;remembers&quot; last project!"
date: 2008-05-25
forum: Programming Talk
---

### Post by haziz on 2008-05-25
I am a newbie at developing in general and in Java in particular with Eclipse (Callisto, 3.2). I am still at the "Hello World" stage or just beyond, I am therefore making small projects and would then ask Eclipse to run them. Unless I delete the last project however Eclipse would insist on running the last project and would refuse to run the more recent project(s). I am setting up a separate project for each short program and therefore have only one main function in each project.
 
Netbeans which I turned to in desperation (v6.01) is acting the way I expect and running the more recent projects and in general behaving as I would expect. Overall I am finding it more intuitive to use.
 
Any advise? Why is Eclipse doing this? How do I convince it to run the most recent project? Should I just stick to Netbeans? People seem to rave about Eclipse in general.
 
Thanks.
 
Sincerely,
 
Hany.

---

### Post by Can+~ on 2008-05-25
You need to make another run setting; click on the side of the green button, choose "Run .." and make a new run setting for the newly created project. Choose the project, choose the main class of said project, and Apply and run.

You can also "Close" (write click on the folder) a project instead of delete it.

Projects and running configurations are two different beasts on eclipse, it does not make a project and a run setting for each; you specify what to run, and how to do it, therefore, you can run multiple projects at the same time, or link them in fancy ways.

---

### Post by achelis on 2008-05-26
Or get the latest version of Eclipse :)

In 3.4 the file you're editing is launched if it has a main-method or a JUnit-test-case. If not the last launched application is launched. 

Can't remember which version of eclipse started doing this.. been with 3.4 for too long I guess :)

---

