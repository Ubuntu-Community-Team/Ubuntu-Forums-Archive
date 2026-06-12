---
title: "[c++] Problem with file i/o and functions"
date: 2010-03-27
forum: Programming Talk
---

### Post by fasoulas on 2010-03-27
In c++

why when i open a file that already has data written in it

```
ofstream out("out.txt") ; 
```

and then when i send it to a function like this

```
update(out , size) ;
```

and then i have an IF statement like this

```
if(pos != size)
        out << somevariable ;

```

i only want data to be written and overwrite the old data to the file only when the if statement is true , otherwise let the file as it is,
but when i ran the code and the if statement was false the file when i opened it was empty.Why this is happening ?

---

### Post by MadCow108 on 2010-03-27
you have to set the open mode to append otherwise it will overwrite the old file
[http://www.cplusplus.com/reference/iostream/ofstream/ofstream/](http://www.cplusplus.com/reference/iostream/ofstream/ofstream/)
ios:app or ios:ate

---

### Post by dwhitney67 on 2010-03-27
> **fasoulas said:**
> Why this is happening ?
Because you are using **ofstream**, and it's primary default behaviour is to create a new file.  There probably a better explanation, but for now, that's the best I have to offer.

Use the regular **fstream** instead, and your app's issues will hopefully go away.

P.S.  Alternatively, test with **ofstream**, but pass **ios::out | ios::in** as the second arg to the constructor.

---

### Post by fasoulas on 2010-03-28
> **dwhitney67 said:**
> 

P.S.  Alternatively, test with **ofstream**, but pass **ios::out | ios::in** as the second arg to the constructor.

with this code my program works ?

but because i want to know what the code does not just copy paste can you explain why this works please ?

so far i know that with this 

```
fstream in("in.txt",ios::out | ios::in ) ;
``` 

means that with this stream you can read and write at the same time

---

### Post by dwhitney67 on 2010-03-28
> **fasoulas said:**
> 
but because i want to know what the code does not just copy paste can you explain why this works please ?


When you open a file with the ios::out mode, you are opening/truncating the "new" file.  You avoid the truncation when you specify ios::in.

In your original post, you did not specify the mode; thus the default for an ofstream is ios::out.

Test the following program, and modify along the way to get a feel to what is really transpiring upon opening the file:
```

#include <fstream>

int main(int argc, char** argv)
{
   using namespace std;

   ofstream file(argv[1], ios::out);
}

```
To compile:
```

g++ file_test.cpp

```
Now, to run, trace through the file so that you can actually see what is going on:
```

strace a.out foo      # foo is the name of the file to be created

```
You should see the following in the output:
```

...
open("foo", O_WRONLY|O_CREAT|O_TRUNC|O_LARGEFILE, 0666) = 3
...

```
Repeat the test, but this time specify ios::out | ios::in, and note the difference with the open() function.

---

### Post by fasoulas on 2010-03-28
thanks a lot for your time , i will try it.
Keep up the good work

---

### Post by rajesh.kanakabandi on 2010-03-28
hi,
i'm new to programming in ubuntu. earlier i used to use windows and turoc3/ide. now i've moved to ubuntu cause of all the restrictions on windows.my problem is that many header files and libraries(graphics) in windows platform are not available here. somebody help me with some pleasant tutorial about the libraries and header files for c/c++ in ubuntu

thank you. :)

---

### Post by dwhitney67 on 2010-03-28
> **rajesh.kanakabandi said:**
> hi,
i'm new to programming in ubuntu. earlier i used to use windows and turoc3/ide. now i've moved to ubuntu cause of all the restrictions on windows.my problem is that many header files and libraries(graphics) in windows platform are not available here. somebody help me with some pleasant tutorial about the libraries and header files for c/c++ in ubuntu

thank you. :)

In the future, please exercise a little "netiquette" by opening a new thread.

To answer your question, a C++ tutorial can be found here:
[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

A good C++ reference guide is also available at the same site:
[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

---

