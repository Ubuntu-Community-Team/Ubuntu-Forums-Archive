---
title: "C++: Threads (serialport communication)"
date: 2006-05-02
forum: Programming Talk
---

### Post by Laterix on 2006-05-02
Hi,

I'm programming my very first C++ application. I need to read data from serial port and write data to it. If I would programm in Java I would use threads to do this.

But what is a common and right way to do this with C++? Should I use POSIX threads though they are really for C or is there some standard way to do this with C++?

Also all tips about serialport communication are welcome!

PS. I have already managed to open connection and send data. :)

---

### Post by LordHunter317 on 2006-05-02
POSIX threads are the only threading mechanism on Linux, so even if you use a C++ wrapper library, you're ultimately making Pthread calls.  Unfortunately, the only stand-alone one I'm aware of, boost::threads, isn't very good.  It has lots of little performance.

The normal way if you don't use threads would be to use asynchronous I/O, which you may have to do anyway depending on your duplexing requirements and such.

---

### Post by lnostdal on 2006-05-02
here's how i do it in C++:
```
#include <iostream>
#include <pthread.h>

using namespace std;


void* callback(void* obj);


class Thread {
public:
int main()
{
 cout << "Hi there" << endl;
 return(0);
}

void run()
{
 pthread_create(&thread, 0, &callback, this);
}

pthread_t thread;
}; // class Thread


void* callback(void* obj)
{
static_cast<Thread*>(obj)->main();
return(0);
} // callback



int main()
{
Thread thread;
thread.run();

return(0);
} // main()
```

remember to link with pthread, or you'll get "mysterious" SIGSEGVs :)

```
g++ -g -Wall -l pthread my_program.cpp -o my_program
```

edit:
then you add the class `Thread' as a superclass of your class, and define a method `main' for it

---

### Post by Laterix on 2006-05-03
Thank you for you replys. Both are very useful. I'm getting into this tonight.

---

### Post by Laterix on 2006-05-03
Okay, I studied serial port communication alot and got it reading incoming messages. I modified the thread example above to fit my program and it works fine, BUT it doesn't keep program running.

I have **while(true) { read from serialport }** inside thread and it starts running in thread, but when my other code gets to end of main function the program exits. What I want is that it would wait until that while has stopped (which is never right now).

---

### Post by LordHunter317 on 2006-05-03
That's because his threading code is wrong.  He never wait()s to ensure the child threads are properly reaped.  I'll post a short C or c++ example if you can't find a pthreads tutorial or figure it out on your own.

---

### Post by lnostdal on 2006-05-03
yeah, you need to make sure the calling thread (here the one running main) blocks/waits untill   the spawned ones are done 

..i guess i somehow assumed people knew this, which is wrong of course .. :)

like this:

```
#include <iostream>
#include <pthread.h>

using namespace std;


void* callback(void* obj);


class Thread {
public:
  int main()
  {
    sleep(3); // sleep 3 seconds before printing message
    cout << "Hi there" << endl;
    return(0);
  }
  
  void run()
  {
    pthread_create(&thread, 0, &callback, this);
  }

  int join()
  {
    return pthread_join(thread, ret);
  }
  
  pthread_t thread;
  void** ret;
}; // class Thread


void* callback(void* obj)
{
  static_cast<Thread*>(obj)->main();
  return(0);
} // callback



int main()
{
  Thread thread;
  thread.run();
  thread.join(); // make sure thread is finished before continuing
  
  return(0);
} // main()

```

check out the man-pages; man 3 pthread_join ..   oh, and there are a couple of pthread-tutorials out there: [http://www.google.no/search?q=pthread+tutorial](http://www.google.no/search?q=pthread+tutorial)

maybe naming the method `waitFor' instead of `join' is better somehow? .. anyhow, that's up to you of course

---

### Post by Laterix on 2006-05-07
Just, wanted to thank. This was very helpful thread for me.

---

### Post by Maddy.Malku on 2011-07-25
Many thanks, very useful information it was.

---

