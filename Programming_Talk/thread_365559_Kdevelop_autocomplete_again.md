---
title: "Kdevelop autocomplete again"
date: 2007-02-19
forum: Programming Talk
---

### Post by sard on 2007-02-19
In 

Project > project options > c++ specific > code completion > code completion databases > custom directory PCS

I've added the '/usr/include/c++/4.1.2/' folder

but code like this won't autocomplete.  Any ideas?:mad: 
```

#include <iostream>
#include <cstdlib>
#include <string>

int main(int argc, char *argv[])
{
  std::string name("Ubuntu");
  name.  // Ctrl Space does nothing after .


  return EXIT_SUCCESS;
}

```

---

### Post by HugoRune on 2007-03-13
I am having the same problems.
Is there any solution for this?

---

### Post by lnostdal on 2007-03-13
that's strange .. it works here .. i've recorded an animation that shows how i enable this here:
[http://nostdal.org/~lars/tmp/kdevelop-autocomplete.gif](http://nostdal.org/~lars/tmp/kdevelop-autocomplete.gif)

---

### Post by polomint on 2007-03-16
Mmm interesting... did you have to press <ctrl> + <space> after typing "blah." to get the list up? I see that you didn't tick the "Automatic code completion" checkbox.

For me the manual <ctrl> + <space> does actually work. but the problem is that the completion list will never pop up on its own, even if the "automatic code completion" box is ticked, which defeats the whole purpose of _automatic_ code completion...

guess I'll just have to live with manual code completion for now :(

---

### Post by lnostdal on 2007-03-16
yes, i hit ctrl-space

---

