---
title: "c++ overload operator&lt;&lt;"
date: 2010-03-29
forum: Programming Talk
---

### Post by WillFerrellLuva on 2010-03-29
Someone please tell me where I am going wrong here.  I want to overload the binary operator << so I can output with my class.  I declared the the overload in a header file:
```

friend std::ostream& operator<<(std::ostream& out, const big_int& show);

```

and defined the overload in an implementation file:
```

ostream& big_int::operator<<(ostream& out, const big_int& show)
...

```

But when I try to compile I get the following error:
```

chris@chris-desktop:~/Code/Projects/Challenge 10$ make
g++ -c -Wall big_int.cpp -o big_int.o
big_int.cpp:84: error: ‘std::ostream& big_int::operator<<(std::ostream&, const big_int&)’ must take exactly one argument

```

Any help would be greatly appreciated.

---

### Post by Simian Man on 2010-03-29
In the header, you declared the function correctly: as a free, friend function.  However in the definition, you gave the function as a member function, which is incorrect.  Change:

```

ostream& **big_int::**operator<<(ostream& out, const big_int& show)
...

```

to:

```

ostream& operator<<(ostream& out, const big_int& show)
...

```

---

### Post by WillFerrellLuva on 2010-03-29
tyvm

---

