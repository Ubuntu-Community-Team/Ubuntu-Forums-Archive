---
title: "[SOLVED] convert float to string"
date: 2008-05-19
forum: Programming Talk
---

### Post by Zeotronic on 2008-05-19
C++: **How do I convert a float into a string?**... or a char array... or whatever?

---

### Post by tamoneya on 2008-05-19
i think the easiest way is to use sprintf();
[http://www.cplusplus.com/reference/clibrary/cstdio/sprintf.html](http://www.cplusplus.com/reference/clibrary/cstdio/sprintf.html)

---

### Post by Wybiral on 2008-05-19
> **tamoneya said:**
> i think the easiest way is to use sprintf();
[http://www.cplusplus.com/reference/clibrary/cstdio/sprintf.html](http://www.cplusplus.com/reference/clibrary/cstdio/sprintf.html)

That is, of course, the idiomatic C way of doing it. But the C++ idiom would have you use a stringstream instead.

---

### Post by Zeotronic on 2008-05-20
> i think the easiest way is to use sprintf();
Yea, I stumbled into that a few minutes after posting...
> But the C++ idiom would have you use a stringstream instead.

I have not heard of this stringstream of which you speak.

---

### Post by dwhitney67 on 2008-05-20
The stringstreams are documented [here]("http://www.cplusplus.com/reference/iostream/").

Here's an example of ostringstream:
[PHP]#include <sstream>     // for ostringstream
#include <string>
#include <iostream>

int main()
{
  const float fltValue = 1234.567890f;
  std::ostringstream ostr;

  ostr << fltValue;

  std::string strValue = ostr.str();

  std::cout << "fltValue = " << fltValue << std::endl;
  std::cout << "strValue = " << strValue << std::endl;

  return 0;
}[/PHP]

P.S.  Does anyone know why the float value gets truncated?  I tried using a double; the same thing happens.

---

### Post by WW on 2008-05-20
A stringstream is like a stream, but it uses a string instead of a file.

Here's some code containing two versions of a conversion function.  One is actually a template that converts "anything" to a string:
[php]
#include <iostream>
#include <string>
#include <sstream>

//
// Use an ostringstream to convert a double to a string...
//

std::string double_to_string(double f)
{
    std::ostringstream s;
    s << f;
    return s.str();
}

//
// By changing "double" to, say, "float" or "int" in the above
// function, you can create other conversion functions.
// This ideas leads directly to the following template, which
// creates a function that converts "anything" to a string.
//

template <typename T>
std::string to_string(const T& value)
{
    std::ostringstream s;
    s << value;
    return s.str();
}
    

int main(int argc, char *argv[])
{
    using std::string;
    using std::cout;

    double d = 2.3456;
    float f = 1.234e-5;
    int k = 9909;
    
    string s0 = double_to_string(d);
    
    string s1 = to_string(d);
    string s2 = to_string(f);
    string s3 = to_string(k);
    
    cout << "s0 = \"" << s0 << "\"\n";
    cout << "s1 = \"" << s1 << "\"\n";
    cout << "s2 = \"" << s2 << "\"\n";
    cout << "s3 = \"" << s3 << "\"\n";
    
    return 0;
}
[/php]

Compile and run:
```

$ g++ -Wall to_string_example.cpp -o to_string_example
$ ./to_string_example 
s0 = "2.3456"
s1 = "2.3456"
s2 = "1.234e-05"
s3 = "9909"
$ 

```

---

### Post by pedro_orange on 2008-05-20
I'm so slow!
You must have this code ready and waiting for unsuspecting questioners!
I'm gonna post meh code anyway so I'm not left out.

```
#include <iostream>
#include <sstream>
#include <string>
#include <iomanip>

int main()
{
float l_float=3.123456789;
std::string l_string;
std::stringstream oss;
oss << std::setprecision(3) << l_float;
l_string=oss.str();
std::cout << "Float as float " << l_float << std::endl;
std::cout << "Float as string " << l_string << std::endl;

return 0;
}
```

```
pedro@pedro-laptop:~/Documents$ g++ -Wall -pedantic brett.c -o brett.o
pedro@pedro-laptop:~/Documents$ ./brett.o
Float as float 3.12346
Float as string 3.12
pedro@pedro-laptop:~/Documents$ 

```

You can set the significant figures of the float to the string using the setprecision() method of the iomanip lib.
I have no idea why the decimal figures are truncated though. Must be a good reason.

---

### Post by WW on 2008-05-20
> **dwhitney67 said:**
> 
P.S.  Does anyone know why the float value gets truncated?  I tried using a double; the same thing happens.

You can override the default output precision of floating point numbers with the **precision** method of the ostringstream.  E.g.
```

  ostr.precision(10);
  ostr << fltValue;

```

---

### Post by Zugzwang on 2008-05-20
> **dwhitney67 said:**
> P.S.  Does anyone know why the float value gets truncated?  I tried using a double; the same thing happens.

It looks like the default precision in the implementation typically bundeled with GNU/Linux is set to such a low value. As you surely know, that can also be changed. ;-) [http://www.cplusplus.com/reference/iostream/manipulators/setprecision.html]("http://www.cplusplus.com/reference/iostream/manipulators/setprecision.html")

---

