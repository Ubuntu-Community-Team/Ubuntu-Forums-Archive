---
title: "C++ casting not working?"
date: 2015-04-15
forum: Programming Talk
---

### Post by bikewrecker on 2015-04-15
Hi guys. Quick question. Does anyone know a reason why simple casting wouldn't work? For example:
```

    int a = 14 % 3;
    cout << "a = "<<  a << endl;
    char c;
    c = (char) a;
    cout << "c = " << c << endl;
    c = static_cast<char> (a);
    cout << "c = " <<  c << endl;
    c = char(a);
    cout << "c = " <<  c << endl;

```

with output 
```

a = 2
c =
c =
c =

```

Thanks in advance!

---

### Post by spjackson on 2015-04-15
The static casting does work, although your program may not do what you want it to do. Each time you print "c = " you following it with the character whose value is 2 (i.e. STX) not the character '2' (whose decimal value is 50). Maybe this is what you mean?
```

    int a = 14 % 3;
    cout << "a = "<<  a << endl;
    char c;
    c = (char) a + '0';
    cout << "c = " << c << endl;
    c = static_cast<char> (a) + '0';
    cout << "c = " <<  c << endl;
    c = char(a) + '0';
    cout << "c = " <<  c << endl;

```

---

### Post by bikewrecker on 2015-04-15
Ah ok. After looking at what you said I did some more research. I when I do "char c = (a + 48)" it works. I'm still a bit confused why though

---

### Post by dwhitney67 on 2015-04-20
> **bikewrecker said:**
> Ah ok. After looking at what you said I did some more research. I when I do "char c = (a + 48)" it works. I'm still a bit confused why though

C and C++ allow for a (signed) char to hold values ranging from -128 to 127.  However, most of the values in this range are not printable characters.  If you examine the ASCII table [man ascii], you will be able to see the values for the printable characters, and a number that are not.  Printable characters range from 32 (SPACE) to 126 (tilde).

C and C++ also allow for you to seamlessly store an actual character to a char variable; for example, you could assign '1' (which is equivalent to 49).
```

char c1 = '1';
char c2 = 49;
assert(c1 == c2);

```
If you want to print a non-printable character in C++, using the std::cout stream, I would recommend casting the char variable to an int.  For example:
```

char c1 = 1;
std::cout << "c1 is: " << (int) c1 << std::endl;

```

P.S.  You should also try to become familiar with the <cctype> / <ctype.h> library functions so that your program can determine whether a char value is printable or of some other type of interest.  Peruse the man-page for 'isprint' [man isprint].

---

