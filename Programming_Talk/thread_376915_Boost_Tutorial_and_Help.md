---
title: "Boost Tutorial and Help"
date: 2007-03-05
forum: Programming Talk
---

### Post by rekahsoft on 2007-03-05
Hi all, i am looking to learn some of the boost library so i can do better parsing of my arguments to main. Currently i use cstring but i was told not to on this forum. Anyways i have heard god thing about it but i do not know exactly where to start. The tutorials on the boost site are good but a little scattered and i am confused on what i am exactly looking for to do the job. Could somebody link me to a good tutorial and maybe give me some example code. Thanks

---

### Post by thumper on 2007-03-05
The link you need to follow is this one: [http://boost.org/doc/html/program_options/tutorial.html](http://boost.org/doc/html/program_options/tutorial.html)

If you have any particular questions, feel free to ping me on freenode.

---

### Post by rekahsoft on 2007-03-05
ok...i will work on it tomorrow after school :D thanks

---

### Post by rekahsoft on 2007-03-06
ok..i have been reading the tutorial and i have some questions. How does the following code work:```
po::options_description desc("Allowed Options");
desc.add_options()
		("about", "Test made by Collin Doering")
		("help", "produce help message")
;
```specificaly how is it possable to have ```
("about", "Test made by Collin Doering")
("help", "produce help message")
``` after the call to add_options()??? also how do i go about compiling a file that contains includes to the boost library? I tried ```
g++ srcfile.cc `pkg-config --libs --cflags boost-1.33`
```but no success

---

### Post by thumper on 2007-03-06
The syntax for program options takes advantage of the wonders of C++ operator overloading and returning references.

Without actually reading the code, they are probably doing something like:
```

...
some_helper add_options()
{
   return some_helper(*this);
}
...

class some_helper
{
   public:
      some_helper(options_description& opts);
      some_helper& operator()(std::string const& name, std::string const& text)
      {
         // save the options
         opts.add_option(name, text);
         return *this;
       }
};

```
So something is overloading the function call operator to do stuff, and returning a reference to something (perhaps itself) that also overrides the function call operator.

'Aint C++ grand?

As far as compiling goes, you need to install the packages: libboost-dev and libboost-program-options-dev.

Then on the command line I think you just need to is to specify the libboost_program_options.so on the command line for g++.

---

### Post by rekahsoft on 2007-03-06
ok..i will give that a try...i forgot about the fact that the () operator can be overloaded...that causes some really wierd behavior...neat...i am still getting used to C++...thanks...i will report back with any problems &| issues

---

