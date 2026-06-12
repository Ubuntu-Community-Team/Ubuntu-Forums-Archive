---
title: "Stuck already"
date: 2007-05-10
forum: Programming Talk
---

### Post by Unholy_goat on 2007-05-10
I know absolutely nothing about programming and have bought a book called beginners guide to c++ i typed in the first example program which is:
//             program 1.1

#include <iostream.h>

void main() 
{
   cout << "Hello! "
                "congratulations on your first"
                "C++ program";
}
and i get a message saying "undefined reference to 'main'" it doesn't say anything in the book about any errors, i'm using vi in terminal, the book seems to be more helpful for DOS users. 
Any help would be appreciated 
Thnak you in advance

---

### Post by ohgod on 2007-05-10
I noticed a few things about this:

-My compiler complained about the depecated include, so I changed it to <iostream>.
-You've got some invalid line breaks in your code (but maybe that was messed up by the forum software).
-the main() function really needs to return an int.  I think a void main is legal in C, but not C++.

Here's what I got to work:
```

#include <iostream>

using namespace std;

int main()
{
  cout << "Hello! Congratulations on your first C++ program" << endl;
  return 0;
}


```

---

### Post by Unholy_goat on 2007-05-10
thank you,
i tried it and it still says "undefined reference to 'main'"  the book uses void main() all the way through

---

### Post by WW on 2007-05-10
Your book appears to be a bit outdated. Check out the comments in [this thread]("http://ubuntuforums.org/showthread.php?t=375812") (near the end of the thread) and [this thread]("http://ubuntuforums.org/showthread.php?t=363492").

---

### Post by Unholy_goat on 2007-05-10
oh ok thank you for your help i shall buy a more upto date one now

---

