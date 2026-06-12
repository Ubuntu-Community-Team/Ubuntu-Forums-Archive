---
title: "Unable to compile my basic pointer code on ubuntu"
date: 2015-06-11
forum: Programming Talk
---

### Post by eto3 on 2015-06-11
[IMG]http://cfile24.uf.tistory.com/original/2131474955795F1A17006C[/IMG]



Hi all!

I wrote my code on Emacs and tried to compile it using clang++ command.
However, as you can see above, I keep coming back to command insert instead of the output.

I will explain anyways in case people cannot see the picture.
So the code I'm trying to compile is

#include <iostream>
using namespace std;

int main()
{
int x = 5;
int *p;
p = &x;
*p = 35;
cout << *p << endl;
cout << x << endl;
return 0;
}

However, when I try to compile this with clang++ pointer.cpp (My emacs file name with the code above is pointer.cpp), there is no output.

one@one-VirtualBox:~$ clang++ pointer.cpp
one@one-VirtualBox:~$ 

.. this is what I get.

I try to input the same command,

one@one-VirtualBox:~$ clang++ pointer.cpp
one@one-VirtualBox:~$ clang++ pointer.cpp
one@one-VirtualBox:~$ 

Yet nothing happens.
Please help me! I am stuck on this and cannot proceed :(

I tried some other pointer codes and basic Hello! (cout examples) stuff and no progress.
The codes I tried are 100% correct since I got them from lecture slides and they work fine with my professor.
I also tried another computer, but got the same result. Is this a problem with virtualbox?

Thank you :)

---

### Post by Bucky Ball on 2015-06-11
*Thread moved to **Programming Talk**.*

Welcome. You'll have to give a lot more info about what exactly you are doing and some output to get any meaningful feedback or help with this. 

I notice you put 'as you can see above'. There is nothing above so perhaps you tried to give more info but it didn't work for whatever reason. Try again. ;)

---

### Post by eto3 on 2015-06-11
[IMG]http://cfile24.uf.tistory.com/original/2131474955795F1A17006C[/IMG]

Thank you for letting me know Bucky!
Hope this image shows up this time..

I will explain anyways in case people cannot see.
So the code I'm trying to compile is

#include <iostream>
using namespace std;

int main()
{
int x = 5;
int *p;
p = &x;
*p = 35;
cout << *p << endl;
cout << x << endl;
return 0;
}

I have similar other codes from my lecture slides that work fine with my lecturer.
However, when I try to compile this with clang++ pointer.cpp (My emacs file name with the code above is pointer.cpp), there is no output.

one@one-VirtualBox:~$ clang++ pointer.cpp
one@one-VirtualBox:~$ 

.. this is what I get.

I try to input the same command,

one@one-VirtualBox:~$ clang++ pointer.cpp
one@one-VirtualBox:~$ clang++ pointer.cpp
one@one-VirtualBox:~$ 

Yet nothing happens.
Please help me! I am stuck on this and cannot proceed :(

I will also modify my original post :)

Thank you!

---

### Post by steeldriver on 2015-06-11
What exactly are you expecting to happen? if the command

```

clang++ pointer.cpp

```

doesn't produce an error message in the terminal, then you should find that it has produced an executable file with the default output name 'a.out' in the current directory

```

$ clang++ pointer.cpp 
$ 
$ ls -l a.out 
-rwxrwxr-x 1 user user 9131 Jun 11 06:11 a.out
$ 
$ ./a.out 
35
35

```

---

### Post by eto3 on 2015-06-11
steeldriver,

I did not know I had to type in the a.out :( I feel so bad.

Thank you very much! I really appreciate your help!

---

### Post by steeldriver on 2015-06-11
If you want to give it a non-default name, you can do that using the -o command line option

```

clang++ pointer.cpp -o myprog

./myprog

```
or
```

clang++ pointer.cpp -o pointer

./pointer

```

You can read more about all the options using the clang manual page

```

man clang

```

where for example you will see

```

       -o file
           Write output to file.

```

---

### Post by eto3 on 2015-06-11
This is so helpful for a beginner like me :)
Thank you!! :oops: much appreciated

---

### Post by flaymond on 2015-06-13
I use *make *to compile my simple C/C++ program.

```

    make myprog

```

and it produce an executable named myprog.

I use this with gcc.

I learn this when I first time found below link.

This resource can be a good way to learn, the hard way. - [http://c.learncodethehardway.org/book/index.html](http://c.learncodethehardway.org/book/index.html)

---

