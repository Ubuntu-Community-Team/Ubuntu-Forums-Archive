---
title: "C++: Trouble with Seq. files"
date: 2010-11-27
forum: Programming Talk
---

### Post by fallenshadow on 2010-11-27
Ive been learning how to work with sequential files in C++ but after I changed my code to pass by parameter in each function my code no longer works.

Any ideas as to why? By the way it might just be the add function thats broken. Its worth fixing that first before anything else.

---

### Post by GeneralZod on 2010-11-27
What "doesn't work" about it? Why do only some of the functions actually open(...) studentFile?

---

### Post by fallenshadow on 2010-11-27
It is supposed to write to a file in the addstudent function but it does not.

> Why do only some of the functions actually open(...) studentFile?

Hmm... I don't know... I guess I didn't think others needed it.

---

### Post by spjackson on 2010-11-27
Well it depends. Sometimes it adds a record and sometimes it does not.

main() opens the file for write, so if the file already exists, all its data is thrown away.

You need to think carefully about when to open the file (and in what mode), when to seek within the file and when to close it, because what you have a the moment is a mess.

Also, you should check whether your read/write/open/close/seek/tell operations are successful and report any error. This will help you pinpoint your bugs.

---

### Post by fallenshadow on 2010-11-28
I ended up fixing the code this morning, now all my three functions work! :D

However Im just having trouble with my last function, which I will post below.

Most likely my logic is all wrong, I think im just getting too confused over it.  :-k

---

### Post by dwhitney67 on 2010-11-28
> **fallenshadow said:**
> 
However Im just having trouble with my last function, which I will post below.


For the sake of being courteous, please show your code within your post; I personally detest having to download files.

But now that I have....

1.  Use the STL string, not char arrays, for gathering your string input:
```

std::string sname;

...
std::getline(std::cin, sname);
...

```

2.  What is "S"?  Is it a class, a typedef, or a typo?

3.  Why are you using strcmp()?

4.  When you open a file for reading (ie. ios::in), there is no need to seek to the beginning of the file; the file pointer is positioned there already.

5.  The read() function of fstream returns the fstream itself, which in turn can be interpreted as a bool value (via the fstream's operator bool() function).  Thus something like this would suffice:
```

while (studentFile.read(reinterpret_cast<char*>(&rec), sizeof(rec)))
{
   // do something with rec
}

```

6.  Lastly, why are you passing an fstream object into the function if you plan to only open and use it from the function itself?  Consider passing the filename to the function (as a const char*).

---

### Post by fallenshadow on 2010-11-29
> 1. Use the STL string, not char arrays, for gathering your string input

We are supposed to use cstring/char arrays.

> 2. What is "S"? Is it a class, a typedef, or a typo?

Its a typedef for a struct.

> 3. Why are you using strcmp()?

We are supposed to use strcmp() to match the variables.

> 4. When you open a file for reading (ie. ios::in), there is no need to seek to the beginning of the file; the file pointer is positioned there already.

Ok, point taken!

> 5. Thus something like this would suffice

Ok I will change that.

> 6. Consider passing the filename to the function (as a const char*).

Im happy with what im doing so far.
---
I would appreciate some help or hints on what to do with the existing code and not just switch to using different methods.

After a name is put in, the program crashes. Thats the main problem!

---

### Post by dwhitney67 on 2010-11-29
> **fallenshadow said:**
> We are supposed to use cstring/char arrays.

Homework?

---

### Post by fallenshadow on 2010-11-29
Anyway, never mind I got it sorted myself! :D

Nothing was majorly wrong with my code but the real problem was calling fstream from within the function brackets. It was better to just use fstream locally.

Thanks for trying to help but right now im just gonna give myself a high five!! 8) \\:D/

---

