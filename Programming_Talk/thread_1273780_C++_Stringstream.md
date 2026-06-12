---
title: "C++ Stringstream"
date: 2009-09-23
forum: Programming Talk
---

### Post by nmccrina on 2009-09-23
Hi all,

I am trying to convert a string into an integer. Of course I could use atoi and be done, but I found this thread that recommended using a stringstream:

[http://ubuntuforums.org/showthread.php?t=396479]("http://ubuntuforums.org/showthread.php?t=396479")

It works, but I don't understand what's happening at all. :( Can anyone maybe explain what's going on? I tried looking at c++reference or whatever that site is, but it didn't really provide any details.

Specifically, I'm curious about the syntax

```
stringstream ss("1234")
```

I assume this is a constructor, but I would think I would be able to do something like this and I can't:
```
stringstream ss;

// stuff

ss("1234");
ss >> i;
```

So do you have to create a new stringstream variable everytime you want to use a stringstream? :confused:

---

### Post by MadCow108 on 2009-09-23
yes stringstream ss("1234") is a constructor which creates s new stringstream object and initialises the buffer with "1234"
but you don't have to create a new object everytime, you can assign a value to the stringstream buffer with the str() member function:
```

stringstream ss;
ss.str("1234");
int i;
ss >> i;

```

the "same" function can also be used to retrieve the content of the buffer when you don't pass an argument:
```

int i=1234;
ss << i;
string str = ss.str() // str is now "1234"

```
the way this works is following:
streams usually have a formated extraction operator >> and an insertion operator << overloaded for various types (the standard streams only have the standard types overloaded)
the insertion operator appends the value on the right side into the stream on the left side. you row multiple of these operators after each other
stream << to_insert << to_insert2
internally this calls some conversion function between the type of to_insert and the type of the stream buffer.

the extraction works in a similar way just it reads some values out of the string buffer which is formated in some way.
the default formating is to skip all whitespaces (space tab newline)
so you can use it like that:
```

ss.str("12 2\t3\n")
int i,j,k;
ss >> i >> j >> k; //i=12 j=2 k=3

```
this searches for a non whitespace character and reads it until it finds the next whitespace and converts it to the type it should extract to.
the next operator starts where the last ended and reads the next number into the next variable.

if a conversion fails (e.g. you try to read a string into an int) the failbit gets set.
this you can check with the fail() function
```

ss("bla");
int i;
ss >> bla;
if (ss.fail()) cout << "extraction failed" << endl;

```

---

### Post by nmccrina on 2009-09-23
Thanks so much, that makes sense! I just tested it and it works. :guitar:

---

### Post by TheBuzzSaw on 2009-09-23
The stringstream object is fantastic. It is a terrific replacement to sprintf and sscanf.

---

