---
title: "error when compiling the most simple socket example"
date: 2007-02-25
forum: Programming Talk
---

### Post by the_nomad on 2007-02-25
im trying to compile the attached archive by using the make command but i get this error:
```
Socket.cpp: In member function &#8216;int Socket::recv(std::string&) const&#8217;:
Socket.cpp:135: error: &#8216;cout&#8217; is not a member of &#8216;std&#8217;
make: *** [Socket.o] Error 1

```

it says it works where i got these files - [here]("http://linuxgazette.net/issue74/tougher.html")
can somebody more experienced in classes please tell me what is wrong in here?!

thanx in advance...

---

### Post by Choad on 2007-02-25
you dont have <iostream> included so you cant use cout

#include <iostream> in socket.cpp and simple_server_main.cpp and it compiles

but i got another wierd error that i have no idea about :S. still compiled tho

---

### Post by the_nomad on 2007-03-03
Thank you dude :) i tried to find by myself what the problem was but it's obviously i need a lot of more practicing and further im pretty confused with these errors in linux... i guess i must start learning them cause i really dont wanna use windows again!!:)

---

### Post by lnostdal on 2007-03-03
hm, just note that this is not a message "from linux" .. it's a message from the c++ compiler -- and you _should_ get the same type of message under windows or in general under _any_ OS using _any_ c++ compiler

furthermore .. at least linux _has_ messages when something suspicious is going on .. that is better than having something that never lets you know what's going on - potentially painting yourself into a corner without noticing as time passes ..

so view these as messages of friendly communication and conversation between you and the compiler instead of petty error messages from something that barely has an interest in talking with you; stuff like that is truly hell to work with :)

actually .. when you compile your code you should ask the compiler to "open up" and give you more messages about potential problems; it should not be shy .. you do this by using the -Wall flag, like this:

```
g++ -o hello -Wall hello.cpp
```

..and you also want to add extra info to your program so your debugging tool can get some more info out of it if something goes wrong .. you do this by using the -g flag, like this:

```
g++ -o hello -Wall -g hello.cpp
```

---

### Post by pravinkharche on 2007-11-27
try i think it works
#include <stdlib.h>

---

