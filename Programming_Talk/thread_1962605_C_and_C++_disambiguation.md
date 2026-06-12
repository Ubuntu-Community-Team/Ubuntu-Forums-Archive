---
title: "C and C++ disambiguation"
date: 2012-04-21
forum: Programming Talk
---

### Post by rafaelcbf on 2012-04-21
Ok, so every time I post a question I always get the same kind of responses, "Don't mix C and C++.", so I want to get this straitened out right now.

[PHP]<stdio.h>=printf/scanf=c[/PHP]
[PHP]<iostream>=cin/cout=c++[/PHP]

Is that right? And, what's wrong with mixing? I'm starting to think my teacher's not really as good as I thought.

---

### Post by zombifier25 on 2012-04-21
Yes, you CAN mix C and C++ code to some extent. However, there ARE some inconsistencies between C and C++, because C++ has grown from an extension of C to a completely different programming language. The following Wikipedia page can explain much better than I can:
[https://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B]("https://en.wikipedia.org/wiki/Compatibility_of_C_and_C%2B%2B")

---

### Post by davetv on 2012-04-21
The wiki article is valid and good but really only touches the surface.

c++ is an "object oriented language"

c is not! (but you can "fudge" it codewise with structures).

c++ can use "new" and "delete" to allocate and deallocate dynamic memory space of structures, arrays and classes. In c you generally use malloc() to allocate memory when needed.

c++ makes it easier : This example will work in c++ but not c

int main() {
  int n=100;
  int* narray=new int[n];
  //....
  delete narray[]; // compiler remembers array size
  return 0;
}
 
also classes do not work in c but are the crux of c++ eg:

class myclass {
  public:
    int SomeFunction() {return 2};
};

int main() {
  myclass *z=new myclass; // new returns a pointer
  int r = z->SomeFunction();     // dereference pointer with -> , r now =2
  delete z;              // delete the memory of this object, compiler knows size
  return 0;
} 

This will not work in c. There are WORLDS of difference.

The language syntax is near identical, but c++ allows the simple creation of objects and memory allocation for arrays that c can't do.

You have lots of reading in front of you. While the syntax is nearly the same, programming in c++ allows a different approach to writing the program where the program itself is probably mostly contained within an object.

I would recommend also that you read up on OOP (Object Oriented Programming) techniques/benefits/methodology.

I think it is quite safe to mix c and c++ source files as long as you are aware of the differences and that c files will compile into a c++ source tree using a c++ compiler (g++) but c++ will not compile with a c compiler (gcc). Ther can be some ambiguities between some common libraries leading to a compile failure, but these are generally sorted by using "define". 

It can be tricky, I think your teacher is teaching you well.

---

### Post by Vaphell on 2012-04-21
at least at the beginning try to not mix things up. While sometimes annoying, it will teach you some coding rigor and attention to detail. Slapping various convenient things together can lead to unholy abominations and it's best not to reinforce such practices ;-)
When you are able to program with ease according to the specs then such restrictions cease to apply.

standard C headers end with .h while standard c++ headers have no extension. C headers are included in C++ std but with dropped .h and with c prefix

[http://en.wikipedia.org/wiki/C_standard_library](http://en.wikipedia.org/wiki/C_standard_library)
[http://en.wikipedia.org/wiki/C%2B%2B_Standard_Library](http://en.wikipedia.org/wiki/C%2B%2B_Standard_Library)

---

