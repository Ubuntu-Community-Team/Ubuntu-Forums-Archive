---
title: "C++ compiling problem"
date: 2009-07-04
forum: Philippine Team
---

### Post by Lila_IT_CMU on 2009-07-04
Hello, I cant compile a C++ code kahit na install ko na ung g++ 

ang output ng terminal is

cout undeclared first use of this function




please help:p

---

### Post by badrra on 2009-07-04
Ay tignan mo yung codes mo tapos debug mo mabuti. Yung function na ginawa mo na ang pangalan "cout" yan ba declared ng tama.

---

### Post by Lila_IT_CMU on 2009-07-04
ok... ano ba syntax mo sa pagcompile ng C++ code?

dba ang cout is output ng iostream? bakit undeclared pa xa? iba ba ung suntax ng C++ sa Windows?

---

### Post by loell on 2009-07-04
that looks like a common error, usually when your compiling without an IDE, if you don't want to study g++ parameters at the momment and just get on with your c++ programming lessons, use an IDE, install anjuta.

---

### Post by Lila_IT_CMU on 2009-07-04
i already have anjuta, but when i Compile my program(Hello World Program) bigla na lng mawala or the program will exit bigla...ano po problem dun???

---

### Post by loell on 2009-07-04
ah yeah, that's because it is being executed directly, i think there's an option there to execute it through terminal so after the program quits, you will still see the terminal.

or..  add cin at the end of your program.

---

### Post by Lila_IT_CMU on 2009-07-05
ah.. that's why, i will try,, thanks a lot
:guitar:

---

### Post by Jucato on 2009-07-05
If that still doesn't work, please try posting your C++ code if it's ok with you. Also, try to install the package **build-essential** instead of g++ alone. You might be missing a few libraries.

@loell: actually, depending on the simplicity of the program, there aren't any special g++ paramaters. A simple "Hello world" C++ program would only need

```
g++ -o hello hello.cpp
```

or even just

```
g++ hello.cpp
```

(the latter will produce an a.out file which can be executed. Legacy Unix naming...)

---

### Post by loell on 2009-07-05
> **Jucato said:**
> 

@loell: actually, depending on the simplicity of the program, there aren't any special g++ paramaters. 


oh ok :D, i just thought there is a need to invoke something for the header/namespace to included at compile time. :)

---

### Post by Lila_IT_CMU on 2009-07-05
i already installed all of the g++ files and libraries...

---

### Post by Lila_IT_CMU on 2009-07-05
#include<iostream>

lila@ubuntu:~/Desktop$ g++ -o 1st 1st.cpp
1st.cpp: In function ‘int main()’:
1st.cpp:9: error: ‘cout’ was not declared in this scope
1st.cpp:9: error: ‘endl’ was not declared in this scope
1st.cpp:10: error: ‘cin’ was not declared in this scope
lila@ubuntu:~/Desktop$ 

#include<iostream.h>

lila@ubuntu:~/Desktop$ g++ -o 1st 1st.cpp
1st.cpp:1:21: error: iostream.h: No such file or directory
1st.cpp: In function ‘int main()’:
1st.cpp:9: error: ‘cout’ was not declared in this scope
1st.cpp:9: error: ‘endl’ was not declared in this scope
1st.cpp:10: error: ‘cin’ was not declared in this scope
lila@ubuntu:~/Desktop$ 

hello, this is the output of the terminal when i compile my c++ code

---

### Post by Jucato on 2009-07-06
Could you please post the full C++ source code?

Also, according to the C++ standard, the standard header files should not have a ".h" extension, so it should be written as

```
#include <iostream>
```

---

### Post by Lila_IT_CMU on 2009-07-06
this is my C++ code


#include<iostream>

int main()
{
     cout << "Hello world" << endl;

     exit(0);
}



thats all

---

### Post by Jucato on 2009-07-06
Ok, a few things to note here:

1. cout and endl belong to the **std** (as in "standard", not the disease) namespace, you need to specify that in your code as well. Kaya hindi sya ma-recognize as valid objects.

There are actually 3 ways to do this.

a. You prepend **std::** to cout and endl like so

```
std::cout << "Hello world" << std::endl;
```

The disadvantage is that it involves too much typing

b. You can, after the #include, instruct C++ that you will be using cout and endl specifically from the std namespace.

```

#include <iostream>
using std::cout;
using std::endl;

```

c. Lastly, you can make a blanket "using" statement to tell the compiler that all functions that don't have an indicated namespace will be from the std namespace:

```

#include <iostream>
using namespace std;

```

This one is the easiest to type, but also has problems, as you will probably learn later on. I suggest sticking to method b.

2. Never use exit() to quit a program normally. exit() should only be used in cases that the program must end *immediately*, like if there was an error. Use **returm** instead:

```
return 0;
```

In the end, your code should look something like this:

```

#include <iostream>
using std::cout;
using std::endl;

int main()
{
    cout << "Hello world" << endl;

    return 0;
}

```

Give it a try. :)

---

### Post by Lila_IT_CMU on 2009-07-06
ok i will try,


akala ko pareho sila sa dev-C++ sa windows...

---

