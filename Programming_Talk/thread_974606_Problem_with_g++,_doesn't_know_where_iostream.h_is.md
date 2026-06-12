---
title: "Problem with g++, doesn't know where iostream.h is..."
date: 2008-11-07
forum: Programming Talk
---

### Post by tylerjw on 2008-11-07
I am trying to compile a very simple C++ program.  For all intents it could be: 
```
#include <iostream.h>
int main (int argc, char **argv)
{
  cout << "Hello world\n";
}
```

I am inputing ```
g++ -c -Wall "HelloWorld.cpp"
``` and I get the error ```
iostrem.h: No such file or directory
```

Please Help, I've done quite a bit of C++ programing in windows but I am just learning linux and I am having trouble compiling my code.

---

### Post by namegame on 2008-11-07
Instead of:

[PHP]#include <iostream.h>[/PHP]

try:

[PHP]#include <iostream>
using namespace std;[/PHP]

---

### Post by tylerjw on 2008-11-07
Thanks man, wow do I feel stupid.  I hate to admit it but even though I've done a decent amount of C++ it was a while ago...

but now I get:
```
 error: expected constructor, destructor, or type conversion before ‘namespace’
```

---

### Post by gpsmikey on 2008-11-07
How did you install the g++ compiler ?? I believe if you did not do the
**sudo apt-get install build-essential**
you will find there is all sorts of stuff missing - I know this is true for the basic gcc compiler.

mikey

---

### Post by tylerjw on 2008-11-07
```
sudo apt-get install g++
```

that's what I used.  I'll try and use what you stated and see what that does.

---

### Post by tylerjw on 2008-11-07
Tried that... get the same error.

---

### Post by slavik on 2008-11-07
post your code as you have it now.

---

### Post by Delever on 2008-11-07
* stupid post deleted *

---

### Post by tylerjw on 2008-11-07
```
#include <iostream>
using namespace std;
int main (int argc, char **argv)
{
  cout << "lots of printing stuff";
  // main purpose of this program is to test if the compiler is working
  // repairing to compile festival text to speech engine.
}
```

---

### Post by LaRoza on 2008-11-07
> **tylerjw said:**
> ```
#include <iostream>
using namespace std;
int main (int argc, char **argv)
{
  cout << "lots of printing stuff";
  // main purpose of this program is to test if the compiler is working
  // repairing to compile festival text to speech engine.
}
```

Well, your problems aside (I don't see how you could have the same error, as you are no longer using *.h), main should be returning and int, and it isn't.

If build-essential is installed, try this:
```

~/p$cat p.cpp
#include <iostream>

int main(int argc, char ** argv)
{
    std::cout << "Hello world" << std::endl;	
    return 0;
}
~/p$g++ p.cpp
~/p$./a.out
Hello world
~/p$

```

Copy and paste any errors.

---

### Post by tylerjw on 2008-11-07
```
HelloWorld.cpp:1: error: expected class-name before ‘/’ token
HelloWorld.cpp:9: error: expected class-name before ‘/’ token
```

---

### Post by LaRoza on 2008-11-07
> **tylerjw said:**
> ```
HelloWorld.cpp:1: error: expected class-name before &#8216;/&#8217; token
HelloWorld.cpp:9: error: expected class-name before &#8216;/&#8217; token
```

Post the code and steps entirely. Like I did.

---

### Post by The Dragon Master on 2010-06-30
Allow me to revive this old thread. My question is general, how do we force a compilaton of an old fashioned (i.e. uses iostream.h) c++ program? My specific example is...

... I want to use an open source c++ program called CaliFloPP, details of this program are here [http://w3.jouy.inra.fr/unites/miaj/public/logiciels/califlopp/#DCUTRI](http://w3.jouy.inra.fr/unites/miaj/public/logiciels/califlopp/#DCUTRI) and downloads are available from here [http://w3.jouy.inra.fr/unites/miaj/public/logiciels/califlopp/form.html](http://w3.jouy.inra.fr/unites/miaj/public/logiciels/califlopp/form.html)
the program is not that old, but still the author used iostream.h as well as an old fashioned dereferencing style.

I am running Karmic on a 64 bit machine, g++ and build-essentials are all installed.

CaliFloPP uses the old fashioned
#include <iostream.h> 
but my g++ can't find that file and neither can locate

DM > locate iostream.h
/usr/include/glib-2.0/gio/gfileiostream.h
/usr/include/glib-2.0/gio/giostream.h

I experimented with minor changes to the source, i.e. removing .h, adding "using namespace std;" but I started getting warnings about the old fashioned dereferencing used in the program. I don't want to re-write the whole thing (I'm not a c++ programer), so how can I force this old fashioned code on a Karmic install of g++? 

thanks
DM

---

### Post by darkprince117 on 2012-12-17
Try ```
#include <iostream>
``` without the ".h". It worked for me.

---

### Post by coffeecat on 2012-12-18
Old thread closed.

---

