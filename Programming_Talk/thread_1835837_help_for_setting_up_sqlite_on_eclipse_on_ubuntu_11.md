---
title: "help for setting up sqlite on eclipse on ubuntu 11.4"
date: 2011-08-30
forum: Programming Talk
---

### Post by avee137 on 2011-08-30
I am a first time user of sqlite and eclipse . I am using ubuntu 11.4 . I need help regarding:
1. installing sqlite on ubuntu.
2.connecting sqlite with eclipse (i.e. settings required to   use sqlite from within a c++ program )

Any help is appreciated. Please post  relevant links and resources,if already available .

---

### Post by vikas.sood on 2011-08-30
Eclipse has nothing to do in connecting to sqlite. I am assuming you are using c++ as the language of your choice. So, you need to link your program to the sqlite lib in order to use it.

1. Install : It must be in the repository. 
    sudo apt-get install sqlite3

2. sqlite3 interface provides APIs for opening sqlite3 database files and manipulating the database and executing dynamically binded queries. You should the documentation on sqlite.org

---

### Post by avee137 on 2011-08-30
> **vikas.sood said:**
> Eclipse has nothing to do in connecting to sqlite. I am assuming you are using c++ as the language of your choice. So, you need to link your program to the sqlite lib in order to use it.

1. Install : It must be in the repository. 
    sudo apt-get install sqlite3

2. sqlite3 interface provides APIs for opening sqlite3 database files and manipulating the database and executing dynamically binded queries. You should the documentation on sqlite.org

Thanks for the reply. I tried testing the existence of header file on the system with following code:
```
#include <iostream>
#include<sqlite3>
using namespace std;

int main() {
    sqlite3 *db ;

    cout << "!!!Hello World!!!" << endl; // prints !!!Hello World!!!
    return 0;
}
```

i get the following error :
```
../src/hello_world.cpp:10:18: fatal error: sqlite3: No such file or directory
compilation terminated.

```

---

### Post by vikas.sood on 2011-08-30
> **avee137 said:**
> 
```
#include <iostream>
#include<sqlite3>
using namespace std;

int main() {
    sqlite3 *db ;

    cout << "!!!Hello World!!!" << endl; // prints !!!Hello World!!!
    return 0;
}
```i get the following error :
```
../src/hello_world.cpp:10:18: fatal error: sqlite3: No such file or directory
compilation terminated.

```
use #include <sqlite3.h>
and link using -lsqlite3

---

### Post by avee137 on 2011-09-10
Thanks.

i got it done.Linking was required.

And there is no connection required . We can use the APIs for sqlite and create and use database with the help of the pointer returned. It is similar in approach to file handling.

'Using sqlite'-the book is a great way to start.

---

