---
title: "How to convert int to char?"
date: 2010-12-22
forum: Programming Talk
---

### Post by leon.vitanos on 2010-12-22
I have an integer and I want to convert it into char but keeping its value!!	!!!
How to do that?

---

### Post by trent.josephsen on 2010-12-22
What?

---

### Post by leon.vitanos on 2010-12-22
> **trent.josephsen said:**
> What?

I changed the question...:D:D:D

---

### Post by PaulM1985 on 2010-12-22
Any particular programming language?

---

### Post by leon.vitanos on 2010-12-22
> **PaulM1985 said:**
> Any particular programming language?

Yes..Sorry C++

---

### Post by hakermania on 2010-12-22
So, you want e.g. 
```
int a = 57
```
 to be converted into 
```
char b = "57"
```
?

---

### Post by PaulM1985 on 2010-12-22
[http://www.cplusplus.com/reference/clibrary/cstdlib/itoa/](http://www.cplusplus.com/reference/clibrary/cstdlib/itoa/)

First link on "convert int to char c++" on google.

---

### Post by dwhitney67 on 2010-12-22
> **PaulM1985 said:**
> [http://www.cplusplus.com/reference/clibrary/cstdlib/itoa/](http://www.cplusplus.com/reference/clibrary/cstdlib/itoa/)

First link on "convert int to char c++" on google.

Oh no, Mr Bill!... that function is non-standard.

If we take the OP literally at his word, then technically only int values ranging from -128 to 127 can be converted to a char; if converting to an unsigned char, then values 0 through 255 can be used.

If the OP meant how to convert an int to an array of chars (aka a string), then the easiest and most portable C++ way is to use the std::stringstream.

```

int value = 12345;
std::stringstream ss;

ss << value;

std::cout << "As a string: " << ss.str() << std::endl;

```

---

### Post by PaulM1985 on 2010-12-22
> **dwhitney67 said:**
> Oh no, Mr Bill!... that function is non-standard.

If we take the OP literally at his word, then technically only int values ranging from -128 to 127 can be converted to a char; if converting to an unsigned char, then values 0 through 255 can be used.

If the OP meant how to convert an int to an array of chars (aka a string), then the easiest and most portable C++ way is to use the std::stringstream.

```

int value = 12345;
std::stringstream ss;

ss << value;

std::cout << "As a string: " << ss.str() << std::endl;

```

Yep, I should have thought of that.  I let a bad day at work get the better of me.

Sorry peeps.  More specifically sorry Bong.Da.City

Paul

---

### Post by worksofcraft on 2010-12-22
OTOH if you want it to be localizable to Hindu-Arabic numerals with a Duodecimal number base to be rendered right to left then you might need something a bit more flexible than stringstream :D

It's a good thing I completed my C++[international numeric formatting library]("http://code.google.com/p/speaknumber/downloads/list") for cases like this :D

---

