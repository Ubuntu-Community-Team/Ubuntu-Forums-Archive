---
title: "C++,Sticky problem with compiling and Character coding"
date: 2009-09-08
forum: Programming Talk
---

### Post by Optimus_Jazz on 2009-09-08
Hi,

I am using gedit to do my C++ programming,however i have run into an issue and don't have much of a clue how to resolve it.
When I compile my program via the terminal using

g++ -g myfile.cpp -o myfile.cpp

and then run it using 

./myfile.cpp

everything works.However,if I reload,or try to reload the file in gedit after it has been compiled and run the code cannot be displayed and i am given this message :
[IMG]http://img38.imageshack.us/img38/7073/cpperror.png[/IMG]

Any ideas on how i might be able to solve this?

---

### Post by MindSz on 2009-09-08
The way you should compile is 

```
g++ -g myfile.cpp -o myprog
```

The way you are doing it makes the compiler create the executable file with the same name as your .cpp file, so it overwrites it.

What I usually do is name the executable the same as my code but without the .cpp extension, so I'd do something like
```

g++ -g myfile.cpp -o myfile
```

---

### Post by Optimus_Jazz on 2009-09-08
Ah i see,thank you, i didnt realise that the last part of the code created the object file.You saved me from ripping my hairout for the next few hours:D

---

### Post by MindSz on 2009-09-08
haha glad to help. We've all been there ;)

---

