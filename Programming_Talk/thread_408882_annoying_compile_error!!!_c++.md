---
title: "annoying compile error!!! c++"
date: 2007-04-13
forum: Programming Talk
---

### Post by rjfioravanti on 2007-04-13
Hey guys, I have been scratching my head on this one for a while... and I can't figure it out. Please take a look and let me know what you think

Fraction.cpp
```

// output on stdout
ostream& operator<< (ostream& out, const Fraction& a) {

	out << a.numerator << "/" << a.denominator ;	
	return out;
}

```

Fraction.h
```

 private:
       
        // variables for saving the numerator and denominator
        int numerator, denominator;

        // output on stdout
        friend ostream& operator<< (ostream&, Fraction&);

```

when I do 

gcc Fraction.cpp

I get

```

gcc      -c Fraction.cpp
Fraction.h: In function ‘std::ostream& operator<<(std::ostream&, const Fraction&)’:
Fraction.h:39: error: ‘int Fraction::numerator’ is private
Fraction.cpp:67: error: within this context
Fraction.h:39: error: ‘int Fraction::denominator’ is private
Fraction.cpp:67: error: within this context
make: *** [Fraction.o] Error 1

```

What is going on!!!

---

### Post by jordanmthomas on 2007-04-13
Is it not an option to put your overloaded << in Fraction.h?

Move it from Fraction.cpp to Fraction.h and it should work.
As the error says, numerator and denominator are private and may only be accessed by functions that are either friends or are in Fraction.h.  So, you have a few options I guess.

---

### Post by g3k0 on 2007-04-13
I generally use g++ with cpp files.....

---

### Post by jordanmthomas on 2007-04-13
Ooh, that too.  :rolleyes:

---

### Post by GeneralZod on 2007-04-14
```
friend ostream& operator<< (ostream&, **const** Fraction&);
```

---

### Post by rjfioravanti on 2007-04-14
ahhh thank you general zod you fixed all my problems!

---

