---
title: "urgent help needed with sqlite3"
date: 2010-09-10
forum: Packaging and Compiling Programs
---

### Post by sherif gamal on 2010-09-10
please, I'm new to database programming but I'm working in a project that makes use of sqlite3.
I know I should #include <sqlite3.h>
but it is not there.... i have just sqlite.h.

can anyone tell me what to do to have the sqlite3 headers and start using them in my programs
Any help will be appreciated.. but please I need some details :)

---

### Post by SevenMachines on 2010-09-10
try,
$ sudo apt-get install libsqlite3-dev

---

### Post by sherif gamal on 2010-09-10
no.. sorry this didn't help.. the library installed but still the sqlite3.h file not recognized.

but i downloaded the sqlite3 package from [http://www.sqlite.org/download.html](http://www.sqlite.org/download.html) and added it's directory to my project's include path.. this made the compiler see the "sqlite3.h" file but the linker says it doesn't find references to the functions... i think it doesn't see the "sqlite3.c" file in the same directory of "sqlite3.h"

if u have any ideas please tell me :)

---

### Post by SevenMachines on 2010-09-10
libsqlite3-dev really is the right package I promise you. It installs to system include directory so it should be found. Can you check its properly installed?

> $ sudo apt-get install libsqlite3-dev

$ dpkg -L libsqlite3-dev|grep /usr/include
/usr/include
/usr/include/sqlite3.h
/usr/include/sqlite3ext.h

$ ls -l /usr/include/sqlite3.h 
-rw-r--r-- 1 root root 282972 2010-09-06 11:52 /usr/include/sqlite3.hSimple (if poor quality :) ) example using a sqlite3 function

temp.c:
> #include <sqlite3.h>

int main (int args, char ** argv){
    int ver = sqlite3_libversion_number();
    printf("Version: %d \n", ver);
    return 0;
}
> 
$ gcc -o temp temp.c -lsqlite3

$ ./temp 
Version: 3007002 


---

