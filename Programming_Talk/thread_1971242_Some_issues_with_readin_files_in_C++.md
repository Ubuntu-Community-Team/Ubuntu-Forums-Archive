---
title: "Some issues with readin files in C++"
date: 2012-05-02
forum: Programming Talk
---

### Post by zombifier25 on 2012-05-02
Hi all. I have a questions which involves reading from a file. Basically, this is the code (I'm keeping it simple for the question, so no file check):
[PHP]
#include <iostream>
#include <fstream>
using namespace std;

int main ()
{
     char x;
     ifstream myfile ("test.txt");
     while (myfile.good())
     {
           myfile >> x;
           cout << x << endl;
     }
}
[/PHP]And for example this is test.txt:
```

a
b
c

```When I run the program above, I get this:
```

a
b
c
c

```Anyway to fix this?
(I know using getline will solve that, but I'm wondering why this happens)

---

### Post by GeneralZod on 2012-05-02
What is the type of 'a'?

---

### Post by zombifier25 on 2012-05-02
> **GeneralZod said:**
> What is the type of 'a'?
Ok, added "char a" into the source.
But it happens with all types however (like int). I still get duplicate last entry.
EDIT: I changed the name of the char a into x.

---

### Post by GeneralZod on 2012-05-02
See e.g.

[http://stackoverflow.com/questions/4533063/how-does-does-ifstream-eof-work](http://stackoverflow.com/questions/4533063/how-does-does-ifstream-eof-work)

Essentially, the eof bit is set only *after* attempting to read pass the end of file (a failing read), and a failing read will not modify the value of x, so in your particular case will still have the value of the last successful read.

Run

```
echo -n "a" > test.txt
```

to get a file containing exactly one char, and run this:

```

#include <iostream>
#include <fstream>
#include <string>
using namespace std;

int main ()
{
     char a;
    
     ifstream myfile ("test.txt");
     while (myfile)
     {
           cout << "Eof before read? " << myfile.eof() << std::endl; // Will always be true, of course, since "myfile" evaluated to true.
           myfile >> a;
           cout << "Read successful? " << !myfile.fail() << std::endl;
           cout << "Eof after read? " << myfile.eof() << std::endl;
           cout << a << endl;
     }
}  

```

---

### Post by cgroza on 2012-05-02
In this case, you should not be checking ios::good to exit the loop because many other things can mess up that flag, not only the end of the file. Use ios::eof and you should be good.

Also, just in case, operator>> reads everything until it encounters a whitespace character and then returns.

---

### Post by DaviesX on 2012-05-02
Here is my "guess"... 
Because myfile.good () tests if the condition of CURRENT file pointer is good or not, but not the next one. Before myfile >> x; is executed, member functions in myfile moves the file pointer to the CURRENT offset, THEN read the actual data. 

when c has already read, the pointer is still the "c" one, then of course it is valid, but when it reaches EOF AFTER the statement in while (), the current pointer is invalid, However, it won't write anything to x.
The result is that it displays the same thing one more time.

---

### Post by DaviesX on 2012-05-02
I don't have that much of proof to my statement, but to change your code a little bit, and it makes sense :)

```

#include <iostream>
#include <fstream>
using namespace std;

int main ()
{
    char x;
    ifstream myfile ("test.txt");

    while ( true )
    {
        myfile >> x;

        if ( myfile.good () )
            cout << x << endl;
        else
            break;
    }
}

```

---

### Post by DaviesX on 2012-05-02
It tests if the current pointer is good before output anything.

---

### Post by 11jmb on 2012-05-02
At the risk of starting a flamewar, you should be mindful of your use of while(true) and break/continue/goto. It's not that these constructs are as inherently evil as your freshman CS professor may preach, but a good rule of thumb is that the conditions of your loops should give you an idea as to what you are iterating over. There are always exceptions, and a rule of thumb is just a suggestion, not a law.

Zod's code will show you a more standard approach. Just test eof after a read, not before.

---

### Post by DaviesX on 2012-05-02
All right, I get it. Btw, what does "CS professor" mean ?

---

### Post by dwhitney67 on 2012-05-02
> **11jmb said:**
> At the risk of starting a flamewar, you should be mindful of your use of while(true) and break/continue/goto. It's not that these constructs are as inherently evil as your freshman CS professor may preach, but a good rule of thumb is that the conditions of your loops should give you an idea as to what you are iterating over. There are always exceptions, and a rule of thumb is just a suggestion, not a law.

+1

> **11jmb said:**
> 
Zod's code will show you a more standard approach. Just test eof after a read, not before.
Ironically, Zod's code reproduces the same issue (error?) that the OP was inquiring about.  Perhaps that was his intent?  Somehow I doubt it.

Anyhow, what I prefer to do is perform the data extraction using the overloaded >> operator method, and then use the return value (the stream itself) for obtaining the status of the stream (note, the stream object itself is converted to a bool value using the overloaded operator bool method).  Something like:
```

#include <iostream>
#include <fstream>
using namespace std;

int main ()
{
     char x;
     ifstream myfile ("test.txt");
     while (**myfile >> x**)
     {
           cout << x << endl;
     }
}

```

---

### Post by zombifier25 on 2012-05-02
+1 all here. I have understood the problem.The eof() flag is set AFTER reading past the file and not before.

And thanks for your code dwhitney67.

---

### Post by lisati on 2012-05-02
> **11jmb said:**
> At the risk of starting a flamewar, you should be mindful of your use of while(true) and break/continue/goto. It's not that these constructs are as inherently evil as your freshman CS professor may preach, but a good rule of thumb is that the conditions of your loops should give you an idea as to what you are iterating over. There are always exceptions, and a rule of thumb is just a suggestion, not a law.

Zod's code will show you a more standard approach. Just test eof after a read, not before.
That sums up what I was taught nicely, i.e. where possible, use conditionals that represent the terminating condition of the loop. It has been a while, but the explanation I was given likely mentioned something like "avoid spaghetti code." 
> **DaviesX said:**
> All right, I get it. Btw, what does "CS professor" mean ?
Computer Science professor.

---

### Post by 11jmb on 2012-05-02
> **DaviesX said:**
> All right, I get it. Btw, what does "CS professor" mean ?

Computer science professor.

@dwhitney67

Thanks for actually compiling and running that, I just assumed it work after a quick read :D

For your function, note that the ifstream returned by the >> operator will have eof, fail, and bad bits, so one thing to be wary of is that it will exhibit the same behavior as good()

---

### Post by 11jmb on 2012-05-02
> **lisati said:**
> That sums up what I was taught nicely, i.e. where possible, use conditionals that represent the terminating condition of the loop. It has been a while, but the explanation I was given likely mentioned something like "avoid spaghetti code." 


Thanks :) 

A quick expansion on why I advise against break/continue: It's not because of computer science reasons. Code with and without these constructs can be logically equivalent. It's more of a software engineering reason: code should be readable. break, continue, and goto make code less readable.

---

### Post by GeneralZod on 2012-05-03
> **dwhitney67 said:**
> 
Ironically, Zod's code reproduces the same issue (error?) that the OP was inquiring about.  Perhaps that was his intent?  Somehow I doubt it.
[/code]

That was, indeed, precisely the intent: note that the code was practically identical except for the addition of detailed debug output and a simpler test-case to show exactly what was going on :)

---

