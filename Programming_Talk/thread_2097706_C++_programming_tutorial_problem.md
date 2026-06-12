---
title: "C++ programming tutorial problem"
date: 2012-12-24
forum: Programming Talk
---

### Post by linuxonbute on 2012-12-24
I decided I would like to learn C++ and started this tutorial

[http://newdata.box.sk/bx/c/index.htm](http://newdata.box.sk/bx/c/index.htm)

Which came from a link in one of the stickies

I hit a problem at the first example which had the line

  cout << "Hello World"

the suggestion from the failed compile using g++

was that the syntax should be

  std::cout << "Hello World"

I am doing this on Ubuntu 12.04

Can someone tell me if this link is out of date or have I got 

something wrong?

Thanks

---

### Post by SuperCamel on 2012-12-24
I can't find a date on that tutorial but iostream.h is depreciated so I suspect it's old and out of date. I suggest you find a different tutorial. 

also, the code should look like this 
```

#include <iostream>

using namespace std;

int main()
{
    cout << "Hello world!" << endl;
    return 0;
}

```

---

### Post by ofnuts on 2012-12-24
> **linuxonbute said:**
> I decided I would like to learn C++ and started this tutorial

[http://newdata.box.sk/bx/c/index.htm](http://newdata.box.sk/bx/c/index.htm)

Which came from a link in one of the stickies

I hit a problem at the first example which had the line

  cout << "Hello World"

the suggestion from the failed compile using g++

was that the syntax should be

  std::cout << "Hello World"

I am doing this on Ubuntu 12.04

Can someone tell me if this link is out of date or have I got 

something wrong?

Thanks

It has recently been stated in another topic in this forum that most C++ tutorials on the web are absolute crap. Find a (recent) book, or at least the site of someone who has published a book. This will weed out the amateurs.

And tutorials don't teach you anything, they just make you a trained monkey.

---

### Post by SledgeHammer_999 on 2012-12-24
In my opinion, the best C++ tutorial on the internet is this: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

It also has very good C++ reference documentation and examples.

---

### Post by linuxonbute on 2012-12-24
All your points seem valid guys:p

I had guessed that it was, at least, out of date.

I have done some php and python coding but wanted to write some stuff to communicate with my Arduino Uno that didn't use processing and C++ looked like it might be okay.

I just tried the code on the site to test it out really and was going to look at a few of them to see which i felt most comfortable with. Also I wanted to get used to the different syntax compared to php and python.

I suppose the stickies could do with updating to weed these useless ones out really.

---

### Post by linuxonbute on 2012-12-24
Part of what I want to do is graph the output from my arduino, displaying the results on the computer.

I can do this quite easily using the processing language but the whole thing seems to be relatively slow if there are a number of calculations to do before displaying the results. 

Can you recommend any libraries to include and, if so, can you point me to any example code for the library please?

---

