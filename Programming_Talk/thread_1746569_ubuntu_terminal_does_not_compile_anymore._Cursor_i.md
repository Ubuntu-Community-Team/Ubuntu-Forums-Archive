---
title: "ubuntu terminal does not compile anymore. Cursor issue"
date: 2011-05-01
forum: Programming Talk
---

### Post by francisco tovar on 2011-05-01
I was compiling a c++ program using ubuntu terminal. Basically using the famous format: dot diagonal name of the programm + enter key, i.e: ./generator (in this case my program name is generator.) By some stupid reason something happened (I guess I pressed the insert key or something similar) and now I can not compile it anymore. The cursor of the terminal is a black square and after typing ./generator + enter, it swaps to the next line of the terminal, rather than giving the instruction of compiling.... How can I toggle the cursor terminal to its back state? I have tried the block num+ insert key, didnt work..
thanks
F

---

### Post by nvteighen on 2011-05-02
> **francisco tovar said:**
> I was compiling a c++ program using ubuntu terminal. Basically using the famous format: dot diagonal name of the programm + enter key, i.e: ./generator (in this case my program name is generator.) By some stupid reason something happened (I guess I pressed the insert key or something similar) and now I can not compile it anymore. The cursor of the terminal is a black square and after typing ./generator + enter, it swaps to the next line of the terminal, rather than giving the instruction of compiling.... How can I toggle the cursor terminal to its back state? I have tried the block num+ insert key, didnt work..
thanks
F

Uh...

```

./generator

```

That doesn't compile the program; it runs it. And chances are that the program isn't showing any output or that it is caught in an infinite loop.

Compiling a C++ program requires something like this (generator being the name of our executable, generator.cpp the source):
```

g++ -o generator generator.cpp -Wall -Wextra -pedantic

```

-Wall -Wextra -pedantic aren't mandatory, but I highly recommend you to use them. These activate all warnings, some extra warnings and some extra strictness... Which is usually a good thing and useful for catching some bugs at compile-time. -Wextra and -pedantic may be more of a personal choice, but general consensus at these forums is that you always should use at least -Wall.

---

### Post by Arndt on 2011-05-02
> **francisco tovar said:**
> I was compiling a c++ program using ubuntu terminal. Basically using the famous format: dot diagonal name of the programm + enter key, i.e: ./generator (in this case my program name is generator.) By some stupid reason something happened (I guess I pressed the insert key or something similar) and now I can not compile it anymore. The cursor of the terminal is a black square and after typing ./generator + enter, it swaps to the next line of the terminal, rather than giving the instruction of compiling.... How can I toggle the cursor terminal to its back state? I have tried the block num+ insert key, didnt work..
thanks
F

Did you happen to enter a character which starts a string, like ' or "? In that case, there ought to be a > prompt on each new line.

If that is what happened, use control-C to break out of it.

Otherwise, kill the window and start another terminal.

---

