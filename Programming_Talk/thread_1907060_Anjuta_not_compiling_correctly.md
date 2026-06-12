---
title: "Anjuta not compiling correctly"
date: 2012-01-10
forum: Programming Talk
---

### Post by paul.strickler on 2012-01-10
Hello,
I just started taking class on C++. In class, we use Visual Studio 2010, but I don't have a windows machine. I am trying to use Anjuta, but am having some trouble. 

I have everything installed, all dependencies resolved, but I can't seem to run my own program. 

When I type:
> 
#include <iostream>
using namespace std;

void main()
{
cout << "test";
}


The 'using namespace std;' is not highlighted like it should be, but everything else is.

I then build it, compile it and run it.
I get this output:
> 
/home/paul/ex2cpp/Debug/src/ex2cpp 
----------------------------------------------
Hello world!

----------------------------------------------
Program exited successfully with errcode (0)
Press the Enter key to close this terminal ... 


No matter what I run- my own code, code from the internet, whatever, I keep getting the "Hello world" message.

I am quite annoyed and would like some help. All this code worked in class!

Thanks.

EDIT: Might help to note that I am on 10.04. Might not, though.

---

### Post by CoffeeRain on 2012-01-10
Are you sure you are compiling or running the right program?

---

### Post by muteXe on 2012-01-11
Are there any project settings in anjuta?
if there are look for something that contains the field "/home/paul/ex2cpp/Debug/src/ex2cpp", as that's what your ide is pointing to when you compile and run.
You might also want to think about running windows in a VM and running visual studio in that to save you a bit of hassle.

---

