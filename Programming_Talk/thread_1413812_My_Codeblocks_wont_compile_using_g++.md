---
title: "My Code::blocks wont compile using g++"
date: 2010-02-22
forum: Programming Talk
---

### Post by Philgaut on 2010-02-22
I've been trying to find how to fix the problem on google for 2 hours and I figured I'd ask here. Sorry if the answer was somewhere on these boards, as you'll probably figure I'm new to ubuntu and I can't find the problem.

So far I did the following commands:

sudo apt-get install build-essential
sudo apt-get install gdb
sudo apt-get install libwxgtk2.6-0

Now the problem I have is when I try to compile this :

[IMG]http://www.learning2code.co.cc/images/problem.png[/IMG]

I figured the problem could be the include path but I can't find how to get it to work..

I ran the following code and it works but I'm trying to follow the learn C++ in 21 days ebook 
and it use the previous code so I'd need to get it to work.

```

#include <iostream>

int main()
{

std::cout << "hello World" << std::endl;
return 0;
}

```

I hope someone can help me to find out what is wrong with my installation.

Thanks!

---

### Post by unknownPoster on 2010-02-22
I see two options.

Include the following line above your main declaration.

```
using namespace std;
```

or continue using:

```
std::cout<<
```


That being said, there is nothing wrong with your installation. You are however, trying to compile invalid code.

---

### Post by Simon17 on 2010-02-22
Also, it ain't <iostream.h>
It's just <iostream>

GET IT RIGHT!

---

### Post by TheBuzzSaw on 2010-02-23
Yeah, #including iostream.h is archaic. You do not place the .h extension on modern C++ libraries.

---

### Post by Philgaut on 2010-02-23
Great thanks a lot, it's working now. 

I had just used the code written in the book I'm using :) Let's hope this book isn't too outdated

---

