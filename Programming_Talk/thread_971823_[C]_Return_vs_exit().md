---
title: "[C] Return vs exit()?"
date: 2008-11-05
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-05
Hello,
I've started learning C to complement my Python. Full Circle Magazine has a series on C that they're doing--where I learned that at the end of the main() block you have to:
```
return 0;
```
Their tutorial isn't done yet though, so some Googling led me to [this one]("http://publications.gbdirect.co.uk/c_book/chapter1/functions.html"), which was written for the new "Standard"
And instead of return 0;, they say you should put:
```
exit(0);

```
which GCC doesn't like.

Is there a good explanation for this?

For now, I'll just replace exit() with return, and move on with my life, but it seems funny that such a basic feature of the language isn't agreed upon.

Thanks.

---

### Post by Tony Flury on 2008-11-05
What error message are you getting when you use exit - you may find that you need to include a header file - <stdlib.h> - to make use of it.

For what it is worth i tend to use return - and never use exit 
It has been suggested that you can use "exit" when you need to finish a program and your program logic is deeply embedded in layers of functions - I would suggest (and this is a personal preference) that you should restructure your code to use return.

If you are writing deamons (that have been forked etc) then you might need to read up, as I think there are special rules on how to exit those programs.

[http://bytes.com/forum/thread212147.html](http://bytes.com/forum/thread212147.html) seems useful - or do a Google search for "Difference between return and exit in C"

At the end of the day it will be a personal style thing

---

### Post by Pentie on 2008-11-05
:popcorn:
there's no difference of using "exit(0)" and "return 0" in the main function.

but if you use "exit(0)" in your subfunction, it will end your whole program, while return will not.

---

### Post by sshuber on 2008-11-05
I thought exit() is along the lines of the pthreads exit where it kills off that task?

---

### Post by fiddler616 on 2008-11-05
> **Tony Flury said:**
> What error message are you getting when you use exit - you may find that you need to include a header file - <stdlib.h> - to make use of it.
Here it is:
> ex1.c: In function &#8216;main&#8217;:
ex1.c:25: warning: incompatible implicit declaration of built-in function &#8216;exit&#8217;


> **Tony Flury said:**
> 
At the end of the day it will be a personal style thing
Unless posts telling me not to, I guess I'll just use return--it seems easier and safer (with regards to not exiting from a subfunction, etc.)

Thanks!

---

### Post by LaRoza on 2008-11-05
return is for returning a function. When main() returns, the program ends with the return value. 

exit() will stop the program no matter where it is called. 

Having unstructured code, especially a program that can be terminated from any random place, is a bad idea.

---

### Post by fiddler616 on 2008-11-05
> **LaRoza said:**
> return is for returning a function. When main() returns, the program ends with the return value. 

exit() will stop the program no matter where it is called. 

Thanks
> 
Having unstructured code, especially a program that can be terminated from any random place, is a bad idea.
Yes.
<off type="topic">You're no longer a mod? *Googles* *Fails* Why?</off>

---

### Post by nvteighen on 2008-11-05
Even if you #include <stdlib.h> to have exit() available, if you don't use **return 0;** in main(), you'll get a compiler error: main has to return an integer... and exit() doesn't qualify as a return statement (even if its behaivor in that place would be the same as returning the value).

---

### Post by crazyfuturamanoob on 2008-11-05
> **fiddler616 said:**
> 
<off type="topic">You're no longer a mod? *Googles* *Fails* Why?</off>

According to this page he still is: [http://sudan.ubuntuforums.com/group.php?groupid=41&pp=10&page=3](http://sudan.ubuntuforums.com/group.php?groupid=41&pp=10&page=3)

---

### Post by nvteighen on 2008-11-05
> **crazyfuturamanoob said:**
> According to this page he still is: [http://sudan.ubuntuforums.com/group.php?groupid=41&pp=10&page=3](http://sudan.ubuntuforums.com/group.php?groupid=41&pp=10&page=3)
...she...

---

### Post by fiddler616 on 2008-11-05
> **crazyfuturamanoob said:**
> According to this page [s]he still is: [http://sudan.ubuntuforums.com/group.php?groupid=41&pp=10&page=3](http://sudan.ubuntuforums.com/group.php?groupid=41&pp=10&page=3)
I remember seeing a post in the Resolution Center a week or so ago asking whether she can have her beans show her membership now. But now I can't find it. And we're getting very offtopic :)
[QUOTE=nvteighen]
*snip*
[/QUOTE]
OK, that makes sense.
This raises the question: why the heck is the tutorial recommending exit?

---

### Post by crazyfuturamanoob on 2008-11-05
> **nvteighen said:**
> ...she...

Oh, sorry. Didn't know that.

---

### Post by LaRoza on 2008-11-05
> **fiddler616 said:**
> 
<off type="topic">You're no longer a mod? *Googles* *Fails* Why?</off>

No. [http://ubuntuforums.org/showthread.php?t=967341](http://ubuntuforums.org/showthread.php?t=967341)

> **crazyfuturamanoob said:**
> According to this page he still is: [http://sudan.ubuntuforums.com/group.php?groupid=41&pp=10&page=3](http://sudan.ubuntuforums.com/group.php?groupid=41&pp=10&page=3)

That is just a group. I started the group, so I don't know if I can leave it...

> **fiddler616 said:**
> I remember seeing a post in the Resolution Center a week or so ago asking whether she can have her beans show her membership now. But now I can't find it. And we're getting very offtopic :)

[http://ubuntuforums.org/showthread.php?t=967773](http://ubuntuforums.org/showthread.php?t=967773)

> 
OK, that makes sense.
This raises the question: why the heck is the tutorial recommending exit?
Because anyone can write a tutorial...

---

### Post by fiddler616 on 2008-11-05
> **LaRoza said:**
> No[...]
That is just a group. [...]


Well, I guess it improves your sanity--though I'll miss your 'Mod Power'

> Because anyone can write a tutorial...
I guess....it just seems kinda funny. Oh well.
From this we learn that:
```
U. Forums > Tutorials
```

---

### Post by supirman on 2008-11-05
In main(), always just use return and not exit(), as there is no point (they're actually the same in this instance).  exit() and return from main will both execute any registered exit handlers and close all stdio streams.  


> **fiddler616 said:**
> Here it is:


Unless posts telling me not to, I guess I'll just use return--it seems easier and safer (with regards to not exiting from a subfunction, etc.)

Thanks!

---

