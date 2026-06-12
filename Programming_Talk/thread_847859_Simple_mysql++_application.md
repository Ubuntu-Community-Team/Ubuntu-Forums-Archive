---
title: "Simple mysql++ application"
date: 2008-07-02
forum: Programming Talk
---

### Post by Khao on 2008-07-02
I'm trying to use the mysql++ api to make a c++ program using it.

I got the api using only apt-get install libmysql++-dev
and I think that's all I need for it.

Then there's my test file (only to test if the include works )
```

#include <stdio.h>
#include <mysql++/mysql++.h>

int main()
{
int x = 2;
}

```

But it doesn't really work.. I'm not very good with gcc and compiling so I was looking around the forums and found a line that looked like it was working but it isn't.
gcc -I/usr/include/mysql -I/usr/include/mysql++ -c MysqlTest.cpp -o MysqlTest
It creates the file, then I chmod it to have execute permission and it says 'cannot execute binary file'
Now I have no idea why it would make a binary file :\
If I try to compile using only gcc MysqlTest.cpp it gives me a loooong list of errors with a ton of 'was not declared in this scope'

I'm good at programming but I don't understand much of how compiling and linking works so be easy on me :P

---

### Post by LaRoza on 2008-07-03
Remove the "-c" flag, which tells it to only compile and not link.

---

### Post by Khao on 2008-07-03
Ok this helped me and I now managed to compile it with the library included!
But I get stuck on another problem.. When I try to make a mysqlpp connection it doesn't work!
Here's the code :
```

#include <mysql++.h>

int main()
{
mysqlpp::Connection conn(false);
}

```

mysqlpp::Connection conn(false); comes right from the mysqp++ example files

and here's the error output :

/tmp/cccp4IsT.o: In function `main':
MysqlTest.cpp:(.text+0xad): undefined reference to `mysqlpp::Connection::Connection(bool)'
MysqlTest.cpp:(.text+0xbb): undefined reference to `mysqlpp::Connection::~Connection()'
collect2: ld returned 1 exit status

Anybody knows what's the problem?

---

### Post by Zugzwang on 2008-07-03
You should definitely look at the "stickies", they tell you about linking and compiling.

In this case, you have to add "-lmysqlpp" to your compiling command since the header files you included just contains the declarations of the functions but does not tell the linker where the definitions are. This is done by telling the linker to include the library "/usr/lib/libmysqlpp.so" which is what this option does.

---

### Post by Khao on 2008-07-03
Woot thanks! :D It took me a few tries but I finally got it! It helped a lot that you told me I needed -lmysqlpp, I then found out I had to add -L/usr/lib since libmysqlpp.so is located in there. If it can help anyone I'm going to post the line used to compile : 

g++ -I../include -I/usr/include/mysql -I/usr/include/mysql++ -L/usr/lib -lmysqlpp Server.cpp -o Server

---

### Post by dwhitney67 on 2008-07-03
You shouldn't have had to specify the -L/usr/lib.

(Edited because the statement, marked in red font, is not true.  /usr/lib is a trusted directory known by 'ldconfig'.  It does not need to appear in /etc/ld.so.conf.
[COLOR="Red"]That directory is already specified /etc/ld.so.conf (or thereabouts).[/COLOR])

Anyhow, if you are "tired" of typing long g++ statements, consider using a Makefile.  Here's one that you can use to build your application:
```
MYSQL_INC := $(shell mysql_config --include)
MYSQL_LIB := $(shell mysql_config --libs)

CXXFLAGS = -Wall -pedantic 

INCPATH  = $(MYSQL_INC) -I/usr/include/mysql++

SRC      = Server.cpp 
OBJ      = $(SRC:.cpp=.o)
EXE      = Server

$(EXE): $(OBJ)
        $(CXX) $(MYSQL_LIB) $^ -o $@

.cpp.o:
        $(CXX) $(CXXFLAGS) $(INCPATH) -c $< -o $@

clean:
        $(RM) $(OBJ)

cleanall: clean
        $(RM) $(EXE)
```
Save this code into a file called Makefile, then run 'make'.  If you copy/paste from this posting, make sure that you preserve the tab-spaces.  Makefiles are very particular about spacings.

---

### Post by Khao on 2008-07-03
Thanks I will try this!
I already know what those makefiles are, I just didn't know how to use them.
And anyway I don't have to copy the whole command everytime I compile since I made myself a little bash script to do this :P

---

### Post by apocalypse_m on 2008-07-26
I recently also had this problem and this post helped me a lot. I did notice however that /usr/lib was not in the general area of my /etc/ld.so.conf

I'm guessing this was also the problem Khao had which caused him to need to use -L/usr/lib in his compilation line.

The solution for anyone new to this is obviously to add the line /use/lib to a .conf file in the whereabouts of /etc/ld.so.conf (ie in there or where it is including from). Please someone correct me if it is wrong to do this (I'm fairly new to some of this linux stuff myself)

Just thought I'd add my findings in case anyone else stumbles across this in their search to get code using mysql++ to compiling.

---

### Post by dwhitney67 on 2008-07-26
I was wrong to state that /usr/lib should be in the /etc/ld.so.conf file.  The /usr/lib and /lib directories are "trusted" directories, that are automatically examined when the 'ldconfig' command is invoked.

Thus it is not necessary to specify /usr/lib when linking your application.  Now, if you add a new library to /usr/lib and fail to run 'ldconfig' afterwards, then there would be a (temporary) reason to specify the -L/usr/lib linker option.

P.S.  'ldconfig' is generally invoked during system start-up, and can also be done manually (with root-permission).  Usually when installing an application using apt-get, 'ldconfig' is the last step that is run.

---

