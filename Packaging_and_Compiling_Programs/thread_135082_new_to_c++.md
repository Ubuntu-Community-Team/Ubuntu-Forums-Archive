---
title: "new to c++"
date: 2006-02-23
forum: Packaging and Compiling Programs
---

### Post by mwanafunzi on 2006-02-23
Hi all,
   This is just to introduce myself on this forum. I am new to programming and I was hoping to get some help. Before I start of with any questions I just wanted make sure that it is ok for me to post my programming questions here. They are very basic questions (as I am a programming virgin). The language that I am learning is c++.

---

### Post by abhaysahai on 2006-02-23
Go ahead and shoot.

---

### Post by mwanafunzi on 2006-02-23
I had a number of question, but i only remeber one....

There was an example on what functions were that I was reading up on, I tried to write it up and compile it. But I got an error.
The cause of the error was that I said

void main()  instead of  int main()

The thing is that in the example they use void main(). My question is why did I get this error. Here is the code, and the error message.

#include <iostream.h>
void newLine()
{
	cout << endl;
}

void main()
{
	cout << "first line" << endl;
	newLine();
	cout << "second line" <<endl;
	
}

The error message


exFunc.cpp:7: error: ‘::main’ must return ‘int’

---

### Post by hod139 on 2006-02-23
The quick answer is that void main() is not legal in C++. It is legal (though bad practice) in C, but the C++ standard requires main to return an int.

Edit: I should also add that you are including a deprecated header. you should be including <iostream> not <iostream.h>

Lastly, this code won't compile even if you fix the return type of main. The cout and endl are defined in the std namespace, and you need to tell your program that. The easiest way for now is to add 
```
using namespace std;
``` to the top of the program.  I have attached a fixed version of your sample.

```

#include <iostream>

using namespace std;

void newLine()
{
    cout << endl;
}

int main(void)
{
    cout << "first line" << endl;
    newLine();
    cout << "second line" <<endl;
    return 0;
}

```

---

### Post by abhaysahai on 2006-02-23
First of all thanks for asking this. I knew that void main () is not supported by c++, but to reply i had to google. 
The various answers are 
1) As per C99 standards the syntax is int main (...),  so it is illegal to use void main....
2) Another good explanation of this 
      In C and C++, the main() function _has_ to return an int, which will
be used by the shell which run the program.  However, with C++, the
return statement isn't mandatory anymore, and a main() function with a
missing return statement will silently return 0.


Guys any more official commens on int main vs void main ???? 

# if u want to program in C++ use #include <iostream>  
   instead of #include <iostream.h> 
    Pay attention to warnings. 

Regards,
Abhay

---

### Post by mwanafunzi on 2006-02-23
thanks for the quick reply,
I did get an message saying that iostream.h is deprecated. I tried using iostream but I got and error message saying

exFunc.cpp: In function ‘void printTime()’:
exFunc.cpp:6: error: ‘cout’ was not declared in this scope
exFunc.cpp:6: error: ‘endl’ was not declared in this scope
exFunc.cpp: In function ‘int main()’:
exFunc.cpp:11: error: ‘cout’ was not declared in this scope
exFunc.cpp:11: error: ‘endl’ was not declared in this scope

So, I kept using iostream.h. 

Anyway, it seems that **using namespace std;** has solved that problem. 

My next question is why is it that with iostream.h there is nothing else to include where as with iostream we have to add using namespace std?

thanks

---

### Post by hod139 on 2006-02-23
[quote=abhaysahai].
2) Another good explanation of this 
      In C and C++, the main() function _has_ to return an int, which will
be used by the shell which run the program.  However, with C++, the
return statement isn't mandatory anymore, and a main() function with a
missing return statement will silently return 0.
[/quote]

This isn't quite true.  In C, main does not have to return an int.  It can return anything.  See [http://homepages.tesco.net/J.deBoynePollard/FGA/legality-of-void-main.html](http://homepages.tesco.net/J.deBoynePollard/FGA/legality-of-void-main.html) for an explanation.

---

### Post by abhaysahai on 2006-02-23
[QUOTE=hod139]The quick answer is that void main() is not legal in C++. It is legal (though bad practice) in C, but the C++ standard requires main to return an int.
[/QUOTE]

Is it legal to use void main () in C ??? I think that in C99 it is illegal, though it is not implemented strictly in gcc, maybe for backward compatibility. 

Please correct me if I am wrong.

---

### Post by hod139 on 2006-02-23
[quote=abhaysahai]Is it legal to use void main () in C ??? I think that in C99 it is illegal, though it is not implemented strictly in gcc, maybe for backward compatibility. 

Please correct me if I am wrong.[/quote] 
See my above post and link ([http://homepages.tesco.net/J.deBoynePollard/FGA/legality-of-void-main.html)](http://homepages.tesco.net/J.deBoynePollard/FGA/legality-of-void-main.html)). Using gcc you will get warnings if you don't use int for the return type, but anything is allowed and it will compile. C++ will throw an error.

---

### Post by hod139 on 2006-02-23
[quote=mwanafunzi]
My next question is why is it that with iostream.h there is nothing else to include where as with iostream we have to add using namespace std?
[/quote] 
1. The iostream.h header is outdated and does not include the namespace protection.  For a quick introduction to namespaces see [http://www.glenmccl.com/ns_comp.htm]("http://www.glenmccl.com/ns_comp.htm") and [http://www.winterdom.com/dev/cpp/nspaces.html]("http://www.winterdom.com/dev/cpp/nspaces.html") (found by google).

2. You didn't **have** to add using namespace std. For this simple example that was the easiest thing to do. Another way you could have written your code is this:
```

#include <iostream>

void newLine()
{
    std::cout << std::endl;
}

int main(void)
{
    std::cout << "first line" << std::endl;
    newLine();
    std::cout << "second line" << std::endl;
    return 0;
} 

```

which is more explicit.

---

### Post by hod139 on 2006-02-23
I should also add that this sub-thread doesn't get nearly as many viewers.  You might be better off posting future questions to the main Programming Talk thread.

---

### Post by mwanafunzi on 2006-02-23
Edit: Just as an example, what programs in ubuntu have been written in C++?

---

### Post by mwanafunzi on 2006-02-23
Thanks for the help guys. I will get to reading the links. I am sure it will take me a while before my next question (while I digest all the info that has been provided. 

Again, thanks.

---

### Post by bored2k on 2006-02-23
[QUOTE=mwanafunzi]Edit: Just as an example, what programs in ubuntu have been written in C++?[/QUOTE]
Gnome is mostly based on C. KDE is mostly based on C++. That's one of the main differences in both of them.

---

### Post by abhaysahai on 2006-02-24
w

---

### Post by abhaysahai on 2006-02-24
[QUOTE=bored2k]Gnome is mostly based on C. KDE is mostly based on C++. That's one of the main differences in both of them.[/QUOTE]

This explains the better memory management in KDE. 
I mean less memory leaks.

---

### Post by hod139 on 2006-02-24
[quote=abhaysahai]This explains the better memory management in KDE. 
I mean less memory leaks.[/quote]

Care to back up these claims?

---

### Post by mwanafunzi on 2006-02-25
I am sure that this is something that I dont have to worry about right now. Why (specifically) are memory leaks a bad thing :-k ?

---

### Post by thumper on 2006-02-27
'cause you run out of memory :)

---

### Post by pharcyde on 2006-03-04
Use STD C++ libraries without .h on the name (i.e. <iostream> instead of <iostream.h>)  Most c libraries are include using the .h and C++ libraries usually follow the convention of not having the .h.

[www.cppreference.com](www.cppreference.com) is a great reference on STD C++ library implementations.

---

### Post by pharcyde on 2006-03-04
[QUOTE=mwanafunzi]I am sure that this is something that I dont have to worry about right now. Why (specifically) are memory leaks a bad thing :-k ?[/QUOTE]

You run out of memory because the space is allocated and then never collected after the program has run.  A good example of this can be seen below.

```
int main(viod)
{
  int *i = new int;
  int *j = new int;
  int *j = new int;
  return 0;
}
```

The three integer pointers will point to dynamically allocated space requested from the O/S.  Once the program is done executing the memory may or may not be reclaimed by the O/S (depends on some things).  This is not particularly bad in this program because u are losing around 32bits per allocation in space everytime this "new int" is called.  This type of programming becomes bad when you have very large dynamic data structures that never get collected.  <- This happens often in some large programs, especially in Windows (Ever remembering having to restart Windows after running large applications?). You can use encapsulating pointer types such as [http://www.cppreference.com/cppmisc/auto_ptr.html](http://www.cppreference.com/cppmisc/auto_ptr.html) or any of the pointers listed in [http://www.boost.org/libs/smart_ptr/smart_ptr.htm](http://www.boost.org/libs/smart_ptr/smart_ptr.htm).  These type of pointers have automatic memory management once they lose their intended scope or when the memory is no longer being pointed to.

---

### Post by zkissane on 2006-03-14
Later on, you may also design some of your own classes that do things like open databases, files, mutexes, GDI objects (in Windows) and/or sockets.  The errors that pharcyde provided "just" leak memory because **int**s don't do anything really dramatic.  Make a mistake like that with, say, a file manipulating class, and you risk corrupting the file, since you don't ever "clean it up" and the OS has a much lower chance of cleaning it up the way you want it.

---

### Post by fizmhd on 2010-03-21
> **pharcyde said:**
> Use STD C++ libraries without .h on the name (i.e. <iostream> instead of <iostream.h>)  Most c libraries are include using the .h and C++ libraries usually follow the convention of not having the .h.

[www.cppreference.com]("http://www.cppreference.com") is a great reference on STD C++ library implementations.


This one works ... 

```

#include<iostream>
using namespace std;
int main()
{
cout<<"HI";
return 0;
}                                                                            


```

---

