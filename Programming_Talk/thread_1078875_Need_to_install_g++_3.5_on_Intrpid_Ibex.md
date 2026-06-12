---
title: "Need to install g++ 3.5 on Intrpid Ibex"
date: 2009-02-23
forum: Programming Talk
---

### Post by DBQ on 2009-02-23
Hi everybody, I need to install g++ version 3.5 on Intrepid.  However, it is not in Synaptic.  I tried adjusting the software sources, but to no avail.

Any ideas?

---

### Post by geirha on 2009-02-23
Why do you need to install a four-five year old version of g++?

---

### Post by DBQ on 2009-02-23
My program, which compiled fine in 8.04 just refuses to compile in 8.10.  I figured that this is a g++ problem :(

---

### Post by dwhitney67 on 2009-02-23
> **DBQ said:**
> My program, which compiled fine in 8.04 just refuses to compile in 8.10.  I figured that this is a g++ problem :(

I haven't even seen your code, but I will go out on a limb and deduce that the problem lies with your code, not with g++.  Would it not be better to correct the issues with your code?

---

### Post by DBQ on 2009-02-23
It would be -- I know that the older versions of g++ forgave things which later versions do not.  I plan to do this.  However, right now I do not have the time to do the whole 9 yards, and I need to run the program.  Is there any temporary workaround? Thank You!

---

### Post by agim on 2009-02-23
Find the 3.5 source code, if its around.
Or install 8.04 as a dual boot or through virtual box.
Maybe you can get real, real lucky and find a g++ 3.5 .deb file.

Don't forget to remove your current g++ before installing the older version.

---

### Post by DBQ on 2009-02-23
I have searched for 3.5 in vain.  I guess my only choice now is to install 8.04.  *sigh*.

---

### Post by dwhitney67 on 2009-02-23
I just upgraded to 8.10 the other day from 8.04; I could be mistaken, but I could have swore that 8.04 had GCC version 4.1.x (or was it 4.2.x?).

Version 3.5 is ancient; but it is probably available at [www.gnu.org](www.gnu.org).

P.S.  I just looked here:  [http://gcc.releasenotes.org/](http://gcc.releasenotes.org/)
There is no version 3.5... was I on a wild-goose chase?

---

### Post by DBQ on 2009-02-24
I though there was.  I just remembered that it was an earlier version. In any case, I figured it out.  Thanks for your help, and sorry about the wild goose. :neutral:

---

### Post by geirha on 2009-02-24
There have been a few changes from the default g++ version (4.2) in Hardy to the default g++ version (4.3) in Intrepid. One of which is what header files get included from iostream.

The following simple c++ program will compile with no warnings on g++-4.2, because including iostream will also include cstdlib which is where srand and rand are declared, but with 4.3 on intrepid, cstdlib is no longer included from iostream.
```
#include <iostream>
int main(void) {
    srand(time(NULL));
    std::cout << "Random number between 1 and 10: " << (rand()%10)+1 
              << std::endl;
    return 0;
}

```

Compiling and running with g++-4.2 on Hardy:
```

$ g++ -Wall test.cpp && ./a.out
Random number between 1 and 10: 9

```
Compiling and running with g++-4.3 on Intrepid
```

$ g++ -Wall test.cpp && ./a.out
test.cpp: In function ‘int main()’:
test.cpp:3: error: ‘srand’ was not declared in this scope
test.cpp:4: error: ‘rand’ was not declared in this scope

```

Including <cstdlib> will make it compile on both, so you probably just need to include some extra headers to make it compile with the latest version.

---

### Post by monkeyking on 2009-02-24
Try posting your compile errors

---

