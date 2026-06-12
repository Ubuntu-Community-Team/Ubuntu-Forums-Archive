---
title: "[C++]how to create files?"
date: 2007-11-13
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2007-11-13
I am a total noob in C++.

How to create files in C++? How to check if a file exists? Is it possible to do it using fstream?

---

### Post by Kadrus on 2007-11-13
Euuh..I might be getting this wrong?But do you want to compile files in C++ or something like that?Run the program that you code?

---

### Post by SledgeHammer_999 on 2007-11-13
Sorry what I meant was how do I create files/folders using C++. Are there any functions that I can use to create a file let's say in "/home/username/sadf.txt"?

---

### Post by Martin Witte on 2007-11-13
take a look at the ofstream class, for an example see eg. [http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html). another useful example is here [http://www.cprogramming.com/tutorial/lesson10.html](http://www.cprogramming.com/tutorial/lesson10.html), it shows also how to check if a file exists

---

### Post by SledgeHammer_999 on 2007-11-13
I have already read this(pretty good tutorials). But this shows me how to output data to an existing file. But I am looking for a way to create a file before being able to output data to that file.

After a quick test a fstream.open doesn't automatically create the file am I passing it.

---

### Post by smartbei on 2007-11-13
Simplest way is using cstdio:
```

#include <cstdio>

using namespace std;

int main()
{
    FILE * file = fopen("newfile.txt","w");
    fprintf(file, "TESTING!!!");
    fclose(file);
    return 0;
}

```

---

### Post by aks44 on 2007-11-13
> **smartbei said:**
> Simplest way is using cstdio

Ans this is supposed to be C++? :-\"
Sorry I couldn't help. :p

The preferred C++ way is to use std::fstreams, or boost::filesystem.

---

### Post by smartbei on 2007-11-13
Haha, true. That doesn't change the  fact that that is the simplest way :).

Anyway, if you are having trouble with fstream, see: [http://www.cplusplus.com/doc/tutorial/files.html](http://www.cplusplus.com/doc/tutorial/files.html)

or (for more newbie-friendly): [http://www.daniweb.com/forums/post31214.html](http://www.daniweb.com/forums/post31214.html)

---

### Post by aks44 on 2007-11-13
> **smartbei said:**
> Haha, true. That doesn't change the  fact that that is the simplest way :).

Duh? This is *even* more simple:

```
#include <fstream>

int main()
{
  std::ofstream file("newfile.txt");
  file << "TESTING!!!";
  return 0;
}
```

Couldn't help again... :p

---

### Post by smartbei on 2007-11-13
=D>
You're right, of course. One line less.

Still, for some reason when I need to quickly write a script in c++ that prints something basic to a file I reach for cstdio. I'll have to work on that :).

---

### Post by SledgeHammer_999 on 2007-11-13
haha this is interesting.

I was using a std::fstream object and fstream.is_open returned false. But now that I used a std::ofstream object ofstream.is_open returns true.

Can I make std::fstream to automatically create the file like std::ofstream does?

---

### Post by aks44 on 2007-11-13
> **smartbei said:**
> One line less.With the added benefit of C++ type safety. :)

> **smartbei said:**
> Still, for some reason when I need to quickly write a script in c++ that prints something basic to a file I reach for cstdio.Indeed, habits are hard to break. Even after 2 years on the project I work on, I still find myself using plain C++ types (int, double, ...) instead of the typedefs we all agreed on (gInt, gReal, ...). Oh well, as long as I remember to search/replace before committing, that doesn't harm anyone... ;)

---

### Post by aks44 on 2007-11-13
> **SledgeHammer_999 said:**
> Can I make std::fstream to automatically create the file like std::ofstream does?

std::ofstream is just a std::fstream with a special constructor. Check both docs, the difference lies in the second parameter (std::ios::cant_remember_what).

---

### Post by Sporkman on 2007-11-14
I use C methodology for IO, myself ( printf, fprintf, fopen, etc. ). I know it, it's simple, and it works.

---

### Post by dwhitney67 on 2007-11-15
> **SledgeHammer_999 said:**
> haha this is interesting.

I was using a std::fstream object and fstream.is_open returned false. But now that I used a std::ofstream object ofstream.is_open returns true.

Can I make std::fstream to automatically create the file like std::ofstream does?

Think of the ofstream as a sub-class of fstream.  If you wanted to use fstream and the is_open() method, then you would need to specify that you are opening the file for "output" when calling the fstream constructor.  For example:

```
fstream myFile( "file.txt", ios::out );

if ( myFile.is_open() )
{
...
}
```

An easier solution is which obviates the need to specify the second constructor arg is:

```
fstream myFile( "file.txt" );

if ( myFile )
{
...
}
```

If you know ahead of time that your file will only be used for output, then use ofstream.  Similarly, if you only plan to read from a file, use ifstream.  In case where writing and reading may be performed on the same file, and you wish to use the same file handle, then use the base fstream.

---

### Post by SledgeHammer_999 on 2007-11-15
This merely works.

Keep in mind that I want to create the file **automatically** if it doesn't exist.

This works as I want:```

fstream myFile( "file.txt", std::ios::out);
```

But this doesn't:```

fstream myFile( "file.txt", std::ios::out|std::ios::in);
```

In the first case the file is created(.is_open=true) in the second it isn't created(.is_open=false).

---

