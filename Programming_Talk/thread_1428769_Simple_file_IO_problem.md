---
title: "Simple file I/O problem"
date: 2010-03-13
forum: Programming Talk
---

### Post by fasoulas on 2010-03-13
How can i make a program in c++ that i will ask the user to enter integers that will be saved in a file , and when user decides to stop entering integers then the program prints their sum and exits.

Is there a way to do this with eof() ??

I prefer to tell me the way to do this and not directly tell me the code.
Any help is welcomed .

---

### Post by MadCow108 on 2010-03-13
its very easy with the iostream library
[http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

just use the formated input operator >> to read ints
the streams don't really care if your reading from file or stdin. So you can use the same code to read/write from your file of numbers of from stdin/stdout

---

### Post by fasoulas on 2010-03-13
> **MadCow108 said:**
> its very easy with the iostream library
[http://www.cplusplus.com/reference/iostream/](http://www.cplusplus.com/reference/iostream/)

just use the formated input operator >> to read ints
the streams don't really care if your reading from file or stdin. So you can use the same code to read/write from your file of numbers of from stdin/stdout

yes i am using the input operator but how can i make the program stop when i want.

I might want to put a smaller or a bigger series of numbers ,not a predefined series of numbers.

For example if the first time i run it i want to put 2 numbers and then make the program in SOME WAY(that is what i can't do) to stop there and find their sum.The second time i run it i might want to insert 5 numbers and then find their sum
and so on....

---

### Post by dwhitney67 on 2010-03-13
Stop iterating based on some condition (e.g. the user enters -1 or the string "quit").

---

### Post by MadCow108 on 2010-03-13
or tell the user to press ctrl + d, which sends EOF, when hes done

a stringstream may come in handy for a string conditional

---

### Post by fasoulas on 2010-03-13
> **MadCow108 said:**
> or tell the user to press ctrl + d, which sends EOF, when hes done

a stringstream may come in handy for a string conditional

```

int main()

{

	int x  ;

	

	ofstream outFile ;

	

	outFile.open("out.txt") ;

	

	while( !outFile.eof() )

	{

		cin >> x ;

		

		outFile << x << "  " ;

	

	}

	

	outFile.close() ;



	cout << endl ;	

	return 0 ;

}

```

i wrote this but the ctrl + D doesn't work

---

### Post by dwhitney67 on 2010-03-13
> **fasoulas said:**
> 
i wrote this but the ctrl + D doesn't work
That is because you are not too bright.

The ctrl-D (or EOF) is applicable to the standard-in stream (cin)... not the file!

---

### Post by fasoulas on 2010-03-13
> **dwhitney67 said:**
> That is because you are not too bright.

The ctrl-D (or EOF) is applicable to the standard-in stream (cin)... not the file!

SO what do you suggest ?

> **dwhitney67 said:**
> That is because you are not too bright.

I am in the learning process you know so your comment about not being bright is not so correct

---

### Post by dwhitney67 on 2010-03-14
```

#include <fstream>
#include <iostream>

int main(void)
{
   using namespace std;

   fstream outFile("out.txt", ios::out);

   if (outFile)
   {
      int x = 0;

      while (cin >> x)
      {
         outFile << x << " ";
      }

      outFile << endl;
      outFile.close();
   }

   return 0;
}

```

---

