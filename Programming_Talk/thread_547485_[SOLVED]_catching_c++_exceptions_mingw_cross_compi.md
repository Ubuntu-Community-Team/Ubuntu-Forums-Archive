---
title: "[SOLVED] catching c++ exceptions mingw cross compiler"
date: 2007-09-10
forum: Programming Talk
---

### Post by drunkyjunky on 2007-09-10
hi,

I have to write a program that runs on windows in c++, therefore i use the mingw cross compiler. But the problem is that I can't catch the exceptions I throw, I can catch them using catch(...) , but in that way I won't be able to see wich exception got thrown.
Does anyone know a solution to this, or does anyone know of a better cross compiler?

thx in advance.

---

### Post by gnusci on 2007-09-10
I really do not know what can be your problem, I do not think [COLOR="Red"]MinGW[/COLOR] can be the problem, 

[http://www.mingw.org/](http://www.mingw.org/)

It is a good compiler, better check the following page and send us the output for one of those examples programs:

[http://www.functionx.com/cpp/Lesson18.htm](http://www.functionx.com/cpp/Lesson18.htm)

---

### Post by ryno519 on 2007-09-10
Could you elaborate on your problem and/or give an example of what you mean? I'm having trouble understanding the problem.

---

### Post by Lux Perpetua on 2007-09-10
I would echo the thoughts of the previous posters. Are you sure your code is correct? If it is, then I'm afraid I can't help, having never cross-compiled for Windows. However, if you're not sure, it can't hurt to post a small example program that demonstrates the issue. If there's a problem, someone will see it.

---

### Post by Wybiral on 2007-09-10
Indeed, because if it's not a bug in your code, then it's a bug in MingW and you should report it. But make sure it's not your code first.

But... Seeing how exceptions are so commonly used in C++, I would expect the MingW people to already know if it were a bug... So it's likely not.

---

### Post by drunkyjunky on 2007-09-19
hi,

sorry for the late reply but I've been on vacation (aaaaahh...).
well, I really do think it's a problem with MingW, I just read your replies fifteen minutes ago and you guys got me doubting, but I've written a really small program which demonstrates the problem : 
```

#include <iostream>
using std::cout;
using std::endl;

class MyException{
};

int main(void){
	try{
		throw new MyException();
	}
	catch(MyException& ex){
		cout << "caught my exception" << endl;
	}
	catch(...){
		cout << "unable to catch my exception" << endl;
	}

	return 0;
}
```

ok, so when I run this code, I get the following output : 
```

unable to catch my exception

```

I think it's correct code, which should output "caught my exception".
Maybe I'm missing something essential here, but I don't think so.
Can anyone who also has a cross-compiler installed (mingw) try this code and show his output? 
Should I report a bug?

thx.

---

### Post by aks44 on 2007-09-19
> **drunkyjunky said:**
> I really do think it's a problem with MingW

Before assuming that a compiler written by professional programmers is at fault, please try to remember: 99% of computer problems sit between the screen and the chair.


> **drunkyjunky said:**
> ```
try{
  throw new MyException();
}
catch(MyException& ex){
  cout << "caught my exception" << endl;
}
```

Indeed, your code is wrong, and MingW is right. You're throwing a MyException* and trying to catch a MyException& .........

The correct syntax is:
```
try
{
  throw MyException();
}
catch (MyException& e)
{
  // whatever
}
```


Or you could also do:
```
try
{
  throw new MyException();
}
catch (MyException* e)
{
  // whatever
  delete e; // dont forget that or you'll get a memleak!!
}
```But this is hardly quality code. What you want is the first solution (throwing an object, not a pointer-to an object).


> **drunkyjunky said:**
> Should I report a bug?

I guess not...

---

### Post by drunkyjunky on 2007-09-19
thanks a lot!!!

I just finished a java project en of course in java you need to throw an exception using new. In java there don't exist pointers....
Didn't know my c++ was so rusty...

---

