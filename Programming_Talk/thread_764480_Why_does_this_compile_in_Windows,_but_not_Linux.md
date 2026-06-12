---
title: "Why does this compile in Windows, but not Linux???"
date: 2008-04-23
forum: Programming Talk
---

### Post by williamburn on 2008-04-23
#include <iostream>
#include <string>
#include <cstdlib>

using namespace std;
string yell = "a dragon is coming, take cover!!!";

int main (void)

{
	cout<< yell.c_str() <<endl
	<< yell.c_str() <<endl
	<< yell.c_str() <<endl
	<< yell.c_str() <<endl;

	return 0;	

}

When i perform my gcc ---

$gcc townCrier.cpp -o townCrier

I get a ton of errors.  Do you think it is possible that my gcc compiler cannot properly find the libraries?  Let me preface my question with these are examples that I am working through c++ for the absolute beginner.  I know, but its the only way i have been able to figure out this c++ thing.

I have ensured that my buildessential is up to date as well.  Any help would be much appreciated as I really dont want to work in windows to learn programming.

Thanks in advance.

---

### Post by jcwmoore on 2008-04-23
try g++,

gcc is the C compiler, g++ is the c++ compiler.

EDIT: i tried your program it worked as expected with g++

---

### Post by tseliot on 2008-04-24
Try compiling it in this way:
```
g++ -ansi -pedantic -Wall townCrier.cpp -o townCrier
```

---

### Post by williamburn on 2008-04-24
Thanks for the reply's.  I am going to try the g++ compiler.  I should have known better and posted the compiler errors.  I thought perhaps the linux c++ syntax may have differed from the windows syntax.  

I will also try the other compiler.

Thank you.  stay tuned for round two.

---

### Post by williamburn on 2008-04-24
Boy, do i feel like a turkey, i was using the wrong compiler.  I was must have gotten my articles mixed up, but my output now works as it should be.

Thanks for the quick replys.  I knew it was something easy, and obviously user error.

---

### Post by JupiterV2 on 2008-04-24
It's not necessary to use the c_str() member function of a string to output it to standard out:

> cout<< yell.c_str() <<endl

Instead, you can simply output the string directly to the output stream.

[PHP]cout << yell << endl;[/PHP]

If your string isn't going to change or be modified, it is always good practice to define it as const to prevent accidentally changing it:

[PHP]const string yell = "a dragon is coming, take cover!!!";[/PHP]

Just some helpful pointers.

Also, its always a good idea to use the CODE or PHP tags around code as in the above examples to make it more readable and distinguishable.

---

