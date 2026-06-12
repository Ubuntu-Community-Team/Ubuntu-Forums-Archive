---
title: "C++ execute/terminate another application"
date: 2009-02-03
forum: Programming Talk
---

### Post by iharrold on 2009-02-03
I am wondering if there is a simple way to execute / terminate an application from a control application.

I have an application which communicates to another application over local sockets.  Every 1/4 second I get a heartbeat message.  If I don't hear that heartbeat message after so many missed instances, I want to try and kill the process then restart it.  

I have the two applications written, I am just trying to figure out how to control them.  And I don't mean to fork() from my current process another child.

---

### Post by jimi_hendrix on 2009-02-03
could always use terminal commands...

system("kill process_name");

---

### Post by iharrold on 2009-02-03
Oh my... Jimi... I honestly didn't even think of doing it like that... 

Much appreciated.:popcorn:

Any idea how to grab the pid of the application?

Nevermind... "killall commandname"

Hrmm... system() is a blocking call.

I.e.
```

std::cout<<"Starting Killapp..."<<std::endl;
std::system("~/workspace/SpawnTester.cpp/Killapp");
  
std::cout<<"Killing Killapp..."<<std::endl;
std::system("killall Killapp");

```

waits on the first system call

Edit... this seems to make it nonblocking...
```

std::cout<<"Starting Killapp..."<<std::endl;
std::system("~/workspace/SpawnTester.cpp/Killapp&");
  
std::cout<<"Killing Killapp..."<<std::endl;
std::system("killall Killapp");

```

---

### Post by dribeas on 2009-02-03
> **iharrold said:**
> 
```

std::cout<<"Starting Killapp..."<<std::endl;
std::system("~/workspace/SpawnTester.cpp/Killapp");
  
std::cout<<"Killing Killapp..."<<std::endl;
std::system("killall Killapp");

```


Adding a & character should help there: 

```

std::system("~/workspace/SpawnTester.cpp/Killapp &");

```

That will make the shell start your Killapp in background and return control to your program right away. Not the cleanest solution, but more of a fast-n-dirty trick.

BTW, you might consider using some scripting language.

---

