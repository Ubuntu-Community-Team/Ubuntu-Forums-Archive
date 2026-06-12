---
title: "very simple scope question in C++"
date: 2007-10-17
forum: Programming Talk
---

### Post by rajan on 2007-10-17
Hi,
i'm trying to learn c++ on my own and I can't find the answer to a simple scope question. I am trying out OO coding practices after using only fortran before so that's where my problem comes up.

I need to take a variable (in this case it's a dynamically allocated array of strings) from a process into it's subroutine. 

ok so I know there's an easy answer to this, but it's not working for me. 


my code is 


    ```


    void writetofile(string filename,int indxx)
    {

      while (count < indxx) // this is line 39 in my code
        {
          cout << filename[count] << "\n";
          count++;
        }
    }

    .......

    int filenum;
    string * filename;
    filename = new (nothrow) string[filenum];

    while (strstr != "break")
      {
        // file each new string input into the array "filename"
        filename[indxx] = strstr;
        indxx++;
        cin >> strstr;
      }

    writetofile(filename,indxx); // this is line 76


```


i get this error at compilation.


```

rajan@paravati:~/Work/C++$ g++-4.0 backup.cpp -o backup
backup.cpp: In function ‘void writetofile(std::string, int)’:
backup.cpp:39: error: ‘indxx’ cannot appear in a constant-expression
backup.cpp:39: error: parse error in template argument list
backup.cpp:39: error: could not convert ‘count<<expression error> >’ to ‘bool’
backup.cpp:41: error: no match for ‘operator[]’ in ‘filename[std::count]’
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/basic_string.h:680: note: candidates are: typename _Alloc::const_reference std::basic_string<_CharT, _Traits, _Alloc>::operator[](typename _Alloc::size_type) const [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
/usr/lib/gcc/i486-linux-gnu/4.0.3/../../../../include/c++/4.0.3/bits/basic_string.h:697: note:                 typename _Alloc::reference std::basic_string<_CharT, _Traits, _Alloc>::operator[](typename _Alloc::size_type) [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>]
backup.cpp:42: error: no post-increment operator for type
backup.cpp: In function ‘void whichfilestobackup()’:
backup.cpp:76: error: conversion from ‘std::string*’ to non-scalar type ‘std::string’ requested
rajan@paravati:~/Work/C++$



```

anyone have any hints? i have been able to pass everything else i have wanted to to another function, but not this. i have already tried to pass by reference (i think you pass by reference by default with arrays anyway), but probably not correctly. 

thanks in advance

---

### Post by gnusci on 2007-10-17
Hello there, here some ideas:

[PHP]
using namespace std; // <------- don't forget this line
    void writetofile(string* filename,int indxx) // <------- here use "string *" 
    // you should use other names, no filename and indxx, for better coding
    {

      while (count < indxx) // this is line 39 in my code
        {
          cout << filename[count] << "\n"; // <----make sure "count" is defined and have a value
          count++;
        }
    }

    .......

    int filenum;
    string * filename;
    filename = new (nothrow) string[filenum];

    while (strstr != "break")
      {
        // file each new string input into the array "filename"
        filename[indxx] = strstr;
        indxx++;
        cin >> strstr;
      }

    writetofile(filename,indxx); // this is line 76
[/PHP]

---

### Post by rajan on 2007-10-17
gnusci,
that's exactly what I needed. i didn't have count defined correctly and i was referencing the wrong aspect of the array. thanks a lot!

---

