---
title: "Shortcut Keys..."
date: 2009-02-18
forum: Programming Talk
---

### Post by Leo Dragonheart on 2009-02-18
Hello, it is my second day of coding. I am doing C++ and all is going well. I am working on loops right now. My question is: Is there a way I can shortcut the [COLOR="RoyalBlue"]g++ -Wall "mycode.cpp" -o executable, chmod u+x executable, ./executable [/COLOR]commands? Or do I have to type them out each time I use them?

---

### Post by simeon87 on 2009-02-18
You could create a shell script and place the relevant instructions in there.

For example:

```

#!/bin/bash

g++ -Wall "mycode.cpp" -o executable
chmod u+x executable
./executable

```

Create a file, make it executable and place the above in it.

---

### Post by Leo Dragonheart on 2009-02-18
> **simeon87 said:**
> You could create a shell script and place the relevant instructions in there.

For example:

```

#!/bin/bash

g++ -Wall "mycode.cpp" -o executable
chmod u+x executable
./executable

```

Create a file, make it executable and place the above in it.

I did as you instructed. How do I use it now? and the g++ -Wall part will I have to make one for every code or is the "mycode.cpp" nuteral? Do you understand that cause I don't even think I understand what I just said...lol

---

### Post by simeon87 on 2009-02-18
> **Leo Dragonheart said:**
> I did as you instructed. How do I use it now? and the g++ -Wall part will I have to make one for every code or is the "mycode.cpp" nuteral? Do you understand that cause I don't even think I understand what I just said...lol

Now you can run it in a terminal. It should be under Accessories > Terminal. Then navigate to the directory where you've got the script (with cd ... to change directory where ... is the name of the directory to change to) and then type the name of the script, for example 'compile' if that's the name of the script.

You can likely use *.cpp to process all .cpp files in a directory, for example:

```

src/*.cpp

```

---

### Post by Leo Dragonheart on 2009-02-18
> **simeon87 said:**
> Now you can run it in a terminal. It should be under Accessories > Terminal. Then navigate to the directory where you've got the script (with cd ... to change directory where ... is the name of the directory to change to) and then type the name of the script, for example 'compile' if that's the name of the script.

You can likely use *.cpp to process all .cpp files in a directory, for example:

```

src/*.cpp

```

Thank you...:)

---

### Post by jimi_hendrix on 2009-02-18
the question was already answered but i have a similar "macro" that i do

i alias clear; make; to compile because i always use makefiles...put the alias in your ~/.bashrc or ~/.bash_profile

---

### Post by Leo Dragonheart on 2009-02-18
> **jimi_hendrix said:**
> the question was already answered but i have a similar "macro" that i do

i alias clear; make; to compile because i always use makefiles...put the alias in your ~/.bashrc or ~/.bash_profile

Thanx jimi, I will try that also...

---

