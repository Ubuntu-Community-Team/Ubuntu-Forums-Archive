---
title: "Configuring Kdvelop to include mysql++ libraries"
date: 2008-09-03
forum: Programming Talk
---

### Post by carolinaswamp on 2008-09-03
Hello all,

I am trying to insert some data into a local mysql database in my program.  i installed the libmysql++-dev package from adept.  i also have libmysql++2c2a, libmysqlclient15-dev, libmysql15off installed.

i added the "-lmysqlpp" library (which is in /usr/lib/) to the target options (LDADD outside the project) for my project.

i re-ran configure and then automake & friends. I am still getting the folowing error when i try to compile:

```
Molecule.cpp:269: undefined reference to `mysqlpp::Connection::connect(char const*, char const*, char const*, char const*, unsigned int)'
```

here is the code i am using:


```
void Molecule::insertIntoDatabase()
{
	
	mysqlpp::Connection conn(false);
	conn.connect("db","localhost","login","pass");
	

 

       

}
```

i have not written anything after this line yet.  the compiler throws the error on conn.connect.  It seems like the word connect is a keyword in c++?

i have #include <mysql/mysql++.h> at the top of my file.  i used mysql/mysql++.h because it is located at /usr/include/mysql++/mysql.h


am i missing a step?  i dont fully understand how to include external libraries in kdevelop. i thought i had done it correctly because the code completion works for the conn object.  thanks for your help.

---

### Post by carolinaswamp on 2008-09-03
if i need to post any more information please let me know.

---

### Post by carolinaswamp on 2008-09-03
i think i fixed the problem.  in kdevelop i had to open the project settings and add these two lines under the configure options:

under c/c++ preprocessor flags i added -I/usr/include/mysql++ which is the location of the header files

under Linker flags i added -L/usr/local/lib which is the location of the mysql++ shared library.

---

### Post by cabalas on 2008-09-03
I hope your fix worked, but just incase I just want to check if you made a typo in your orginal post where you said:

> **carolinaswamp said:**
> 
i have #include <mysql/mysql++.h> at the top of my file.  i used mysql/mysql++.h because it is located at /usr/include/mysql++/mysql.h


are you sure you didn't mean 
```
#include <mysql++/mysql++.h>
```
Someone correct me if I'm wrong but I think once you added the c++ preprocessor flag you should just be able to go ```
#include<mysql++.h>
```

---

