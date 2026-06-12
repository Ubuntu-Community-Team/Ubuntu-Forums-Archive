---
title: "postgres and lipqxx"
date: 2009-02-02
forum: Programming Talk
---

### Post by Barney_awesome on 2009-02-02
hello!
i am trying to use postgres with the libpqxx. in order to avoid building libpqxx from scratch, i download the packages libpq4 and libpqxx2.5.5 which i think are properly installed. i am trying to compile the "test" program given in the readme file from libpqxx which is the following: 

	#include <iostream>
	#include <pqxx/pqxx>

	using namespace std;
	using namespace pqxx;

	int main()
	{
		try
		{
			connection C;
			cout << "Connected to " << C.dbname() << endl;
			work W(C);

			result R = W.exec("SELECT name FROM employee");

			cout << "Found " << R.size() << "employees:" << endl;
			for (result::const_iterator r = R.begin();
			     r != R.end();
			     ++r)
			{
				cout << r[0].c_str() << endl;
			}

			cout << "Doubling all employees' salaries..." << endl;
			W.exec("UPDATE employee SET salary=salary*2");

			cout << "Making changes definite: ";
			W.commit();
			cout << "ok." << endl;
		}
		catch (const exception &e)
		{
			cerr << e.what() << endl;
			return 1;
		}
		return 0;
	}

and i try to compile it like that ->  g++ -o test.o test.cpp -lpqxx

obviously i am missing something b/c the msg i get is that:
 pqxx/pqxx: No such file or directory

can anyone help me pls?

---

### Post by cabalas on 2009-02-02
Off the top of my head are you sure that there isn't meant to be a pqxx/pqxx.h?

---

### Post by Barney_awesome on 2009-02-02
this is the source code of the example given by lipqxx. i dont think that there is a problem with the code, (i tried what you said with no result), but that there is a problem with either the built of the libqpxx or the command i am trying to execute (the flag -lpqxx at the end). obviously libpqxx is not recognized as a library :(

---

### Post by cabalas on 2009-02-02
sorry it seems in my haste on the last post I didn't have a good look at the command you are using, it appears that you are not setting the include path for the postgresql library try using the following command to compile it.

```
g++ -o test.o test.cpp `pkg-config --cflags libpqxx` `pkg-config --libs libpqxx`
```

I haven't tested this so it may need some tweaking but I am pretty sure it will work.

---

