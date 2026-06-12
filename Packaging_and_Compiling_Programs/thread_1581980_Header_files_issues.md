---
title: "Header files issues"
date: 2010-09-25
forum: Packaging and Compiling Programs
---

### Post by praetoriaen on 2010-09-25
Hello, this is my first post here so I'll just skip to the point.
How can I make gcc and g++ include third party headers? Because I'm having a little project of my own with ARToolKit and I can't compile any of the example files because of "undefined reference to xxx" error. So I searched around, found something about using -l and -L but I don't understand it.. so can someone please tell me what to do?

---

### Post by SevenMachines on 2010-09-29
Main options to use with gcc/g++ are 
>  -I/path/to/headers/    Which tells the compiler to include that directory when it searches for header files from your code
>  -L/path/to/libraries/Tells the compiler  to include that directory when it searches for libraries used by your code. 
You'll then tell it to link to a library with
>  -lmylibThis links to a library called something like libmylib.so or something like that

So, for example. If I created a special library libmyspecialstuff with the headers 
/usr/local/include/myspecialstuff.h

and the library in
/usr/local/lib/lbmyspecialstuff.so

The used it in my program 
maintest.c 
> #include <myspecialstuff.h

int main (int args, char ** argv){
 .... use some myspecialstuff functions here
return 1;
}
Then the gcc command would be something like
gcc -I/usr/local/include -L/usr/local/lib -lmyspecialstuff -o maintestprog maintest.c

---

