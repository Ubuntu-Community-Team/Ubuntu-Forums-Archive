---
title: "C++ ofstream::open won't accept string as a filename"
date: 2013-04-28
forum: Programming Talk
---

### Post by chellrose on 2013-04-28
I'm including iostream, fstream, string, and cstdlib headers.  In my program, if I have

```

ofstream os;
string file = "infoFile.txt";

os.open(file, ios::app);

```

upon compilation I see the error

```

NoteOrganizer.cpp:28:31: error: no matching function for call to ‘std::basic_ofstream<char>::open(std::string&, const openmode&)’
NoteOrganizer.cpp:28:31: note: candidate is:
/usr/include/c++/4.6/fstream:702:7: note: void std::basic_ofstream<_CharT, _Traits>::open(const char*, std::ios_base::openmode) [with _CharT = char, _Traits = std::char_traits<char>, std::ios_base::openmode = std::_Ios_Openmode]
/usr/include/c++/4.6/fstream:702:7: note:   no known conversion for argument 1 from ‘std::string {aka std::basic_string<char>}’ to ‘const char*’

```

but if I instead do

```

os.open("infoFile.txt", ios::app);

```

it compiles and runs just fine.  I've used strings as file names countless times before, though, with no trouble at all.  What is going wrong?
(BTW: I'm using g++)

Thanks! :)

---

### Post by SledgeHammer_999 on 2013-04-28
As the error message says to you there isn't an open() method which accepts std::string. The open() method has this signature [b]void open( const char *filename,
           ios_base::openmode mode = ios_base::out );[/b] So you could do:
```
os.open(file.c_str(), ios::app);
```

Or make gcc use the C++11 standard which has a suitable open() function which takes an std::string. I believe you have to use the "-std=c++11" switch when compiling.

Relevant info on open()->[http://en.cppreference.com/w/cpp/io/basic_ofstream/open](http://en.cppreference.com/w/cpp/io/basic_ofstream/open)

---

### Post by chellrose on 2013-05-01
Right!  I forgot about the c_str().  ](*,)

Thanks!

***note to all: This thread is solved... Once I figure out how to get the "prefix" option back, I'll mark it solved for real :)

---

### Post by Tony Flury on 2013-05-02
You can mark a thread as [SOLVED] by using the Thread Tools (near the top of the page).

---

### Post by chellrose on 2013-05-02
That's how I used to do it (in the old forum), but that option doesn't appear under Thread Tools now.  Is there another trick that I'm missing?

---

