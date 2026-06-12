---
title: "Quick question about c++"
date: 2006-10-29
forum: Programming Talk
---

### Post by thenetduck on 2006-10-29
Hi, 
  I am trying to put a class in c++ called Fraction (two of them) inside of a class called Expression. When I do this as a pointer ie.


 ```

  class Expression
   {
      public:
      private:
         Fraction* frac1; 
         Fraction* frac2;
   }


```

 It gives me this error.


hw10.cpp:15: error: ISO C++ forbids declaration of ‘Fraction’ with no type
hw10.cpp:15: error: expected ‘;’ before ‘*’ token


I don't know what to do or how to fix it. I have to use a pointer to a class for my CS165 class. Does anyone know what i'm doing wrong and more importantly, how to fix it? 

 Thanks,
  The Net Duck

---

### Post by yabbadabbadont on 2006-10-29
You have to either prototype or define the Fraction class *before* you use it anywhere else.

---

### Post by thenetduck on 2006-10-29
> **yabbadabbadont said:**
> You have to either prototype or define the Fraction class *before* you use it anywhere else.

Sorry for the ignorance, but how can I do that? BTW thanks for the help, 
 
The Net Duck

---

### Post by yabbadabbadont on 2006-10-29
We're not here to do your homework for you...  :D [-X 

Good luck on your class.

---

### Post by po0f on 2006-10-29
thenetduck,

Declare Fraction in a header file and include it in Expression's header file.

---

### Post by thenetduck on 2006-10-29
Thanks!

---

### Post by rplantz on 2006-10-29
> **thenetduck said:**
> Sorry for the ignorance, but how can I do that? BTW thanks for the help, 
 
The Net Duck

Many students do not realize that each source file (your "active" code) is compiled one at a time. After each is compiled, the resulting machine code is then linked together (along with a bunch of libraries) to produce the executable file (application).

In your example, you have probably declared your Fraction class in a header (.h) file. Every place you declare a Fraction object, you need to #include the header file that declares the Fraction class. Otherwise, when the file that uses your Expression class gets compiled, the compiler doesn't know about the Fraction class.

You should ask your teacher (professor, ta, etc.) to explain this to you. I'm a retired CS professor, so I know that a lot of students have problems with using header files, but the concepts are very important.

---

### Post by po0f on 2006-10-29
thenetduck,

The reason why it works that way is because the compiler will then know what a Fraction is and will allow Expression to contain a pointer to it.  You might have been able to get away with something like this even:
```
class Fraction;  // forward declaration

class Expression {
  Fraction *f1;
  Fraction *f2;
};

class Fraction {
  /* definition here */
};
```

---

### Post by thenetduck on 2006-10-30
> **rplantz said:**
> Many students do not realize that each source file (your "active" code) is compiled one at a time. After each is compiled, the resulting machine code is then linked together (along with a bunch of libraries) to produce the executable file (application).

In your example, you have probably declared your Fraction class in a header (.h) file. Every place you declare a Fraction object, you need to #include the header file that declares the Fraction class. Otherwise, when the file that uses your Expression class gets compiled, the compiler doesn't know about the Fraction class.

You should ask your teacher (professor, ta, etc.) to explain this to you. I'm a retired CS professor, so I know that a lot of students have problems with using header files, but the concepts are very important.

How I didn't know that. Thanks for the enlightenment! :D

---

### Post by thenetduck on 2006-10-30
> **po0f said:**
> thenetduck,

The reason why it works that way is because the compiler will then know what a Fraction is and will allow Expression to contain a pointer to it.  You might have been able to get away with something like this even:
```
class Fraction;  // forward declaration

class Expression {
  Fraction *f1;
  Fraction *f2;
};

class Fraction {
  /* definition here */
};
```


Sweet thanks, I just tried that way also and it worked very nice. :cool: 

 Sweeter than pie, 
 
Thanks, The Net Duck

---

