---
title: "Help with sqlite3 sample code"
date: 2008-12-25
forum: Programming Talk
---

### Post by dosterror on 2008-12-25
Hey all im a newb and I need some help compiling sqlites sample code.
Now lets say I have 2 files: main.c that has the sample code from [http://www.sqlite.org/quickstart.html](http://www.sqlite.org/quickstart.html), and sqlite-3.6.7.so.
How would I link the shared library and compile main.c using gcc? Ive tried everything and it keeps giving me the "sqlite3.h not found" error.
THanks!

---

### Post by stevescripts on 2008-12-26
1. Have you installed build-essential ?

2. Can you post the output of your attempt - it should build pretty easily on ubuntu 

Steve

---

### Post by stevescripts on 2008-12-26
Finding a couple of minutes - assuming you have build-essential installed - and if you saved the c file as, say sqlitetest.c - try the following command line:

```


gcc sqlitetest.c -o sqltest -lsqlite3


```

You will get a couple of warnings, but you will have an executable

Steve

---

### Post by dosterror on 2008-12-26
Thanks! I needed build-essentials installed!

---

### Post by dosterror on 2008-12-28
so the problem persists. i have the latest build-essential version.
now i tried to compile with the command you suggested but im getting

/usr/bin/ld: cannot find -lsqlite3
collect2: ld returned 1 exit status

i also tried compiling with the source and this is what i get:

sqlite3.o: In function `pthreadMutexAlloc':
sqlite3.c:(.text+0x329a): undefined reference to `pthread_mutexattr_init'
sqlite3.c:(.text+0x32ad): undefined reference to `pthread_mutexattr_settype'
sqlite3.c:(.text+0x32ca): undefined reference to `pthread_mutexattr_destroy'
and so on...

what is going on? help!

---

### Post by mike_g on 2008-12-28
Sounds like you installed sqlite3 but not the sqlite development libraries. Take a look in the repos for something like sqlite3-dev and install it.

---

### Post by stevescripts on 2008-12-29
As mike_g said, you should install the dev libraries - pretty easy with Synaptic.

If you want to build the latest sqlite from source you need the sqlite-3.6.7.tar.gz file from [http://www.sqlite.org/download.html](http://www.sqlite.org/download.html)

The directions to build it are included.  If you have any trouble extracting/building/installing from source, feel free to post back here.  Plenty of expertise around here to get you going.

Steve

---

### Post by mrallaire on 2011-12-04
UPDATE - Sorry for posting to an old thread. I too had problems compiling the sqlite3 sample program from [http://www.sqlite.org/quickstart.html](http://www.sqlite.org/quickstart.html). It is a program demonstrating how to use the C/C++ API interface to SQLite. Basically it lets you create your own program in C/C++ that uses a database with sqlite3.

Error message during compiling: cannot find -lsqlite3

Solution identified by &#65279;mike_g: install the development libraries

UPDATE: There is no &#65279;sqlite3-dev file, instead install the hard to find lib&#65279;sqlite3-dev from the Synaptic Package Manager.

Using Ubuntu 10.10 Maverick Meerkat 



If anyone is still having troubles, here is a more detailed walkthrough. 

1. In the Synaptic Package Manager, install sqlite3, libsqlite3-dev, and gcc (compiler).

2. Go to the sqlite3 website at: [http://www.sqlite.org/quickstart.html](http://www.sqlite.org/quickstart.html). Scroll down to the last bit of code, the example written in C.

3. Copy the code and paste it into a new text file.  Name that file sqltest.c.

4. Delete the line numbers on each line. Save and exit.

5. Open the terminal, and navigate to the directory with the sqltest.c file you just created.

6. Compile by typing: gcc sqlitetest.c -o sqltest -lsqlite3

7. type ./sqltest to run

---

### Post by ep_ on 2011-12-07
Same problem here on 11.10 (AMD 64).  "libsqlite3-dev" is installed and the newest version.  This used to work. What am i missing?  
 
ep@ephome:~/develop/sqltest$ cat sqlite3test.cpp 
#include <iostream>
#include <sqlite3.h>

int main()
{
    sqlite3 *db;
    int retval = sqlite3_open("DELETE_ME.db", &db);
    if (retval == SQLITE_OK)
        sqlite3_close(db);
    return 0;
}

ep@ephome:~/develop/sqltest$ g++ -Wall -lsqlite3 sqlite3test.cpp -o sqltest
/tmp/ccU0HshU.o: In function `main':
sqlite3test.cpp:(.text+0x15): undefined reference to `sqlite3_open'
sqlite3test.cpp:(.text+0x2a): undefined reference to `sqlite3_close'
collect2: ld returned 1 exit status
ep@ephome:~/develop/sqltest$ g++ -Wall -lsqlite3 sqlite3test.cpp -o sqltest
/tmp/cceQwrui.o: In function `main':
sqlite3test.cpp:(.text+0x15): undefined reference to `sqlite3_open'
sqlite3test.cpp:(.text+0x2a): undefined reference to `sqlite3_close'
collect2: ld returned 1 exit status

---

### Post by ep_ on 2011-12-07
Nevermind, order is important, if instead I do

g++ -Wall sqlite3test.cpp -o sqltest -lsqlite3

It compiles and links with no errors.  Not sure why, somebody might explain that.

---

