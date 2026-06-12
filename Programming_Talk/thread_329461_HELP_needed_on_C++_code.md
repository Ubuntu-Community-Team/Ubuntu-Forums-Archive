---
title: "HELP needed on C++ code"
date: 2007-01-01
forum: Programming Talk
---

### Post by vze4p6c2 on 2007-01-01
Hey guys, what is wrong with this code??
```

//Theoretically, this program simple outputs:

//START...


#include <iostream>

class Ratio {
public:
Ratio(void):top_speed(0), top_distance(0), top_score(0) {start(void);}
protected:
double top_speed, top_distance, top_score;
void start(void) {std::cout<<"START..." << std::endl;}
};


int main(void) {
Ratio boat_1;
return 0;
}

```

I get the GCC compiler error:
```

code.cpp: In constructor ‘Ratio::Ratio()’:
code.cpp:10: error: expected primary-expression before ‘void’

```

Thanks a lot.

---

### Post by Wybiral on 2007-01-01
You must be comming in from the C world, in c++, if a function doesn't require any parameters, you don't put "void" as a parameter. This should compile...

```

#include <iostream>

class Ratio {
public:
Ratio():top_speed(0), top_distance(0), top_score(0) {start();}
protected:
double top_speed, top_distance, top_score;
void start() {std::cout<<"START..." << std::endl;}
};


int main() {
Ratio boat_1;
return 0;
}

```

---

### Post by vze4p6c2 on 2007-01-01
oh wow, so simple... Thanks a lot man.

---

### Post by hod139 on 2007-01-02
> **Wybiral said:**
> You must be comming in from the C world, in c++, if a function doesn't require any parameters, you don't put "void" as a parameter. This should compile...


There is nothing wrong with specifying void in the parameter list of a function, and in fact I do it all the time just for extra clarity.  The problem with the code was stated explicitly in the error message and is when he calls the start function.  You can't **pass** void as an argument to a function.  The only thing that has to change is line 10 with the removal of void from the call to start, the line would look like:
```

Ratio(void):top_speed(0), top_distance(0), top_score(0) {start();}

```
Then the code would compile.

---

### Post by Wybiral on 2007-01-02
Yeah, but it's really just unnecessary code to type to have to put void in all parameterless functions. I actually wasn't even aware you could declare them with void as a parameter, I thought that was strictly a C thing.

---

### Post by hod139 on 2007-01-02
> **Wybiral said:**
> Yeah, but it's really just unnecessary code to type to have to put void in all parameterless functions. I actually wasn't even aware you could declare them with void as a parameter, I thought that was strictly a C thing. Most people will probably agree with you.  The only reason void is in C++ parameter lists is because of C and backwards compatibility.  In C void f() and void f(void) are different.

---

### Post by Houman on 2007-01-02
Hi there;

Here is an interesting bit of info about the f() versus f(void) problem: [http://www.parashift.com/c++-faq-lite/newbie.html#faq-29.4](http://www.parashift.com/c++-faq-lite/newbie.html#faq-29.4)

A direct quote from the FAQ: > the f(void) style has been called an "abomination" by Bjarne Stroustrup, the creator of C++, Dennis Ritchie, the co-creator of C, and Doug McIlroy, head of the research department where Unix was born.

regards

Houman

---

