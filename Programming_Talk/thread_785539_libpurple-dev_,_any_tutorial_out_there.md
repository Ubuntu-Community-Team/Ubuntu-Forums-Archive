---
title: "libpurple-dev , any tutorial out there?"
date: 2008-05-07
forum: Programming Talk
---

### Post by StOoZ on 2008-05-07
Im looking desperately for a tutorial/guide for this , as I would like to develop a simple terminal IM client for ICQ only,with a simple features such as : see who is only, for a particular account + send msg,thats it.

does any one knows of a good tutorial?

---

### Post by xelapond on 2008-05-07
What language do you want to write it in?  Is there a specific reason you want to use libpurple-dev, or would any other ICQ lib work?

---

### Post by StOoZ on 2008-05-07
in C++.
I dont know any other lib, I would be happy to know a one which have more tutorials and guides.
the reason for this app is for learning,write some code in C++.
it supposed to be a terminal only client,no gui,and very simple,as already mentioned.

---

### Post by StOoZ on 2008-05-07
*bump*
someone? :(

---

### Post by loell on 2008-05-07
libpurple is written in c , I guess you need to read the pidgin source code  to understand its core. yup, no docs for new developers.

---

### Post by StOoZ on 2008-05-08
arent there another libs for that purpose?

---

### Post by loell on 2008-05-08
kopete's core libraries maybe.

---

### Post by slavik on 2008-05-08
pidgin.im has the docs, if you can, Sean Egan published a bug on GAIM (version 1.5 I think it was) that shows how to do some stuff with the library (the library is pretty much the same).

---

### Post by StOoZ on 2008-05-09
couldnt find anything useful about koepte.
regarding libpurple, I manages to find this 
[http://developer.pidgin.im/doxygen/2.2.0/html/group__core.html]("http://developer.pidgin.im/doxygen/2.2.0/html/group__core.html")

it is a great source,but still not a tutorial, since I dont really know how to begin with it.
:(

---

### Post by michaelcbrook on 2010-05-20
I know this thread is extremely old, but I feel that it is still a relevant problem that libpurple has little or no tutorials out there. That is why I would like to share a website that I am starting called [http://libpurple.com/](http://libpurple.com/). It is very new, but I plan on providing tutorials and how-to's for libpurple as well as examples on how to connect it with databases, etc. for web based services and the like.

Hopefully this will help someone...

-Michael

---

### Post by nvteighen on 2010-05-20
> **StOoZ said:**
> couldnt find anything useful about koepte.
regarding libpurple, I manages to find this 
[http://developer.pidgin.im/doxygen/2.2.0/html/group__core.html]("http://developer.pidgin.im/doxygen/2.2.0/html/group__core.html")

it is a great source,but still not a tutorial, since I dont really know how to begin with it.
:(

Usually, libraries don't have tutorials, except very standard ones like ncurses, GTK+ or QT, but the others have API docs... like the ones you've found. Understanding API documentation is an important skill for a programmer and as far as I see, that one is very nicely organized.

---

### Post by go_beep_yourself on 2010-09-20
&#10140;  CBomber  tar -xf pidgin-2.7.3.tar.gz 
&#10140;  CBomber  cd pidgin-2.7.3  
&#10140;  pidgin-2.7.3  find ./ -name purple-client-example.c 
./libpurple/purple-client-example.c 
&#10140;  pidgin-2.7.3 


As described here:
[http://stackoverflow.com/questions/1705250/getting-started-with-libpurple](http://stackoverflow.com/questions/1705250/getting-started-with-libpurple)

---

