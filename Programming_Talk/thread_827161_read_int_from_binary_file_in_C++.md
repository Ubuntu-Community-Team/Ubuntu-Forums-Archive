---
title: "read int from binary file in C++"
date: 2008-06-12
forum: Programming Talk
---

### Post by arido4 on 2008-06-12
Hello,

I have just started studying C++, come from a Java background, and need to develop a routine to read from a binary file different sizes of data (read a char, read an int, read a short, etc).

C++ STL offers me fstream.read ( char* s, streamsize n );

It is not a problem to read a char using this function: just pass the destination char and it is done.

However, I am trying to read an int from this function. I tried this:

```

char intToBeRead[4];
fstream.read(intToBeRead, 4);

```

Okay, now I got the 4 bytes that make up an integer. Now, how do I convert this char array to an int?

```
int intvalue = (int) intToBeRead; 
```

doesn't seem to work.

I apologize if this is a stupid question. I know the solution must be really simple. Any help will be appreciated.

Thanks

---

### Post by xlinuks on 2008-06-12
Hi,
```

 int n, sum = 0;
  while (inFile >> n) {
      sum += n;
  }

```
I took it from here:
[http://pages.cs.wisc.edu/~hasti/cs368/CppTutorial/NOTES/IO.html](http://pages.cs.wisc.edu/~hasti/cs368/CppTutorial/NOTES/IO.html)

---

### Post by scourge on 2008-06-12
I don't think you need a char array at all. You can read the data straight to an int:

```

int x;
myFile.read((char*)&x, sizeof(int));

```

---

