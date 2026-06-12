---
title: "Cout During Cin"
date: 2011-07-11
forum: Programming Talk
---

### Post by roadkillguy on 2011-07-11
I have a threaded function that handles sockets and other miscellaneous things in my server program (c++).  I have my main function set up to handle user input.  It works just fine, until my thread decides to cout a message or warning.  Everything I have typed is then flushed after the warning is flushed.

```
mycommand arg1 arWARNING!!
Invalid command.
```

While this is logically what the program should do, it gets annoying that your commands are effectively destroyed.  My thinking is that I should have a print function, that stores cin, writes the message, and then writes what you had back into cin.  The problem with this is that A. There is no way to read the current value of cin without blocking (Waiting for the \n) and B. There is no way I have found to write back into cin.

How do I effectively manage messages and commands on the command line?

---

### Post by dwhitney67 on 2011-07-11
You do have options...

1.  Direct standard out to a file, which then can be displayed in a separate terminal ( tail -f <filename> )

2.  Use ncurses so that you can have a separate areas within the terminal for output and input.

However, the first thing I would do is to examine your program to discover the BUG!  Standard output will NOT affect standard input.  It may mess with what is displayed on the terminal, but not with the streams themselves.

Here's a simple program that mimics the issue you described.  If you enter the word 'quit', and then wait for the 'WARNING' message to be displayed.  After wards, press the Enter key (for a newline).
```

#include <pthread.h>
#include <unistd.h>
#include <string>
#include <iostream>

void* thread(void* arg)
{
   while (true)
   {
      sleep(5);
      std::cout << "WARNING" << std::endl;
   }
}

int main()
{
   pthread_t tid;

   pthread_create(&tid, NULL, thread, NULL);

   std::string input;

   while (input != "quit")
   {
      std::getline(std::cin, input);
   }

   pthread_cancel(tid);
   pthread_join(tid, NULL);
}

```

---

### Post by roadkillguy on 2011-07-11
I didn't realize that they only mess with each other visually.. I must have a bug somewhere else then.

Thanks for writing that code :D

What does apt-get use when it shows the percentage of the currently downloading file?  Somehow it writes directly to the terminal, and I think I could use something like that.

---

### Post by dwhitney67 on 2011-07-11
apt-get may very well be using a carriage return in lieu of a newline.  For instance:
```

#include <iostream>
#include <unistd.h>

int main()
{
   for (int i = 0; i <= 100; i += 10)
   {
      std::cout << ".................. " << i << "%**\r**";
      std::cout.flush();
      sleep(1);
   }
   std::cout << std::endl;
}

```

---

### Post by roadkillguy on 2011-07-11
Hmmmm that's pretty cool, but I'm afraid that doesn't stop it from clearing the appearance of cin.  I was hoping they were somehow writing straight to the terminal data:(.  I'll probably have a look at ncurses.

---

