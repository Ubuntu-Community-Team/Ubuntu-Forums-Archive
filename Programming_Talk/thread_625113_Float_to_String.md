---
title: "Float to String"
date: 2007-11-27
forum: Programming Talk
---

### Post by EzarKun on 2007-11-27
Hi,
I am a C++ newb, can anyone write up  a piece of code that converts a float variable into a string.
Say I had a float var:

```
float var1 = 34.3212;
```

I want to convert it to a string, and the string when put to the terminal should look like this

```
String of Float = 34.32
```

that is I was a precision of 2. 

Thanks everybody.

---

### Post by Wybiral on 2007-11-27
[http://cppreference.com/stdio/sprintf.html](http://cppreference.com/stdio/sprintf.html)

You can set the precision with the standard printf formating (it's on that site too).

EDIT:

Ooops... Sorry, I thought you were using C. In that case: [http://cppreference.com/cppsstream/index.html](http://cppreference.com/cppsstream/index.html)

---

### Post by aks44 on 2007-11-27
To convert a float to a std::string, use [std::stringstream]("http://www.cplusplus.com/reference/iostream/stringstream/").

To directly output a float to the console, use [std::cout]("http://www.cplusplus.com/reference/iostream/cout.html").

Both have the necessary methods to control the formatting (including the precision).

Specifically, see [std::ios_base::precision()]("http://www.cplusplus.com/reference/iostream/ios_base/precision.html") and [std::ostream::operator<<()]("http://www.cplusplus.com/reference/iostream/ostream/operator%3C%3C.html").

---

### Post by EzarKun on 2007-11-27
thanks for the quick replies, see what I can do.

---

### Post by EzarKun on 2007-11-27
sorry for the bother again, but I am stuck with the precision bit.
When I say
setprecision(2) for a value like 32.341212
the result is 32
I was 32._34_, that is the 2 numbers after the decimal, for the use of currency.
thanks.

---

### Post by adelgado on 2007-11-27
Try setting the precision at 4 :-)

Greetings

---

### Post by aks44 on 2007-11-27
From [std::ios_base::precision()]("http://www.cplusplus.com/reference/iostream/ios_base/precision.html") documentation (relevant parts in bold, follow the links in the documentation for more details):
> The floating-point precision determines the maximum number of digits to be written on insertion operations to express floating-point values. How this is interpreted depends on whether the ***floatfield*** **format flag** is set to a specific notation (either **fixed** or **scientific**) or it is unset (using the default notation, which is neither fixed nor scientific):

    * On the default floating-point notation, the precision field specifies the maximum number of meaningful digits to display in total counting both those before and those after the decimal point. Notice that it is not a minimum and therefore it does not pad the displayed number with trailing zeros if the number can be displayed with less digits than the precision.
    * In both the **fixed** and **scientific** notations, the precision field specifies exactly **how many digits to display after the decimal point**, even if this includes trailing decimal zeros. The number of digits before the decimal point does not matter in this case.



> **adelgado said:**
> Try setting the precision at 4 :-)
And have 1234.56 be output as 1234? :-p

---

### Post by EzarKun on 2007-11-27
> **aks44 said:**
> From [std::ios_base::precision()]("http://www.cplusplus.com/reference/iostream/ios_base/precision.html") documentation (relevant parts in bold, follow the links in the documentation for more details):





And have 1234.56 be output as 1234? :-p

hey thanks, it works

---

### Post by iharrold on 2007-11-27
```
 

#include <iostream>
#include <sstream>

int main (void)
{
    float val1 = 0.1091;

   std::ostringstream buffer;
   buffer <<std::fixed<<std::precision(2)<<val1;
   std::string some_string = buffer.str();

   std::cout<<some_string<<std::endl;
   return 0;
}


```

Hrm... too slow.. very too slow.

---

### Post by aks44 on 2007-11-28
> **iharrold said:**
> Hrm... too slow.. very too slow.

Slow? Compared to what? Have you done measures? :-\"

---

### Post by iharrold on 2007-11-28
> **aks44 said:**
> Slow? Compared to what? Have you done measures? :-\"

Heh.. meant my reply, not the code.

---

### Post by aks44 on 2007-11-28
> **iharrold said:**
> Heh.. meant my reply, not the code.

LOL sorry for the confusion. :)

---

