---
title: "Threaded C++ Programming with Boost"
date: 2010-12-03
forum: Programming Talk
---

### Post by Tristanm1 on 2010-12-03
I'm experimenting with threads in C++ at the moment, and have been using the Boost libraries to do it. So far everything is working fine. The problem I have is that the program I'm writing draws to the screen in one thread and reads user input in another. The graphical thread is a thread made with a class. It runs a loop controlled by a boolean variable. What I have tried to do is have the input thread, upon receiving the keystroke required to tell the program to end, call a method in the threaded class that changes the boolean value and then wait for that thread to end. This doesn't work. The graphical thread continues to run as if the boolean hadn't been changed. 

My question is what is the proper way to send a signal to a thread?

---

### Post by dwhitney67 on 2010-12-03
One important aspect of boost threads is that it makes a _copy_ of your thread class object.  Thus, even if you pass the address (or even reference) of your Drawing thread to your Input thread, it won't matter one iota because boost is employing a distinct Drawing thread.

Consider defining a semaphore (eg. a bool value) that is shared by each thread class.  This in turn can be used to control the flow of the application.  For example:
```

class Drawer
{
public:
   Drawer(bool& sem) : quit(sem) {}

   void operator()()
   {
      while (!quit)
      {
         ...
      }
   }

private:
   bool& quit;
};

class Input
{
public:
   Input(bool& sem) : quit(sem) {}

   ...

private:
   bool& quit;
};

int main()
{
   bool quit = false;

   Drawer drawer(quit);
   Input  input(quit);

   boost::thread* t1 = new boost::thread(drawer);
   boost::thread* t2 = new boost::thread(input);

   ...
}

```
When your Input thread detects that the user has entered "quit", set the semaphore to true.  Both the Input thread and the Drawer thread should then act accordingly to exit when the semaphore is set to true.

---

