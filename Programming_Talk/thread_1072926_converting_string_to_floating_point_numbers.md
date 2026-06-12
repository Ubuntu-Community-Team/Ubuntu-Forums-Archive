---
title: "converting string to floating point numbers"
date: 2009-02-17
forum: Programming Talk
---

### Post by monkeyking on 2009-02-17
I'm quite puzzled by this small program, can someone elaborate why the following program gives different results

[PHP]
#include <iostream>
#include <sstream>

///convert string to double
double to_double(std::string a){///@param a is the string to convert.
  double str;
  std::stringstream ss;
  ss<<a;
  if(!(ss>>str)){
    printf("Error converting :\"%s\" will exit\n",a.c_str());
    exit(0);
  }
  ss>>str;
  return str;///@return The double value.
}

///Convert string to float.
float to_float(std::string a){///@param a is the string to convert.
  float str;
  std::stringstream ss;
  ss<<a;
  if(!(ss>>str)){
    printf("Error converting :\"%s\" will exit\n",a.c_str());
    exit(0);
  }
  ss>>str;
  return str;///@return The float value.
}


int main(){
  std::string var = "147541611";
  printf("%s <-> %f\n",var.c_str(),to_double(var));
  printf("%s <-> %f\n",var.c_str(),to_float(var));
  return 0;
}
[/PHP]

output

```
./a.out 
147541611 <-> 147541611.000000
147541611 <-> 147541616.000000

```
The to_float function doesn't work but a 9 digit number should still be within the limit of a float?

thanks in advance

---

### Post by jpkotta on 2009-02-17
[http://en.wikipedia.org/wiki/Single_precision](http://en.wikipedia.org/wiki/Single_precision)

According to that, floats don't have enough precision for 9 decimal digits.  Most of the time, you should use doubles.  On some architectures, doubles are actually faster, because single precision calculations are done as double precision and then rounded.

---

### Post by dwhitney67 on 2009-02-17
@ OP -

The problems you are encountering may stem from the generic use of the std::stringstream, versus using a specialized version, such as std::istringstream.

Try instead:
```

double to_double(std::string& str)
{
  std::istringstream iss(str);
  double dbl;
  iss >> dbl;
  return dbl;
}

```

------------------------------------------------------

EDIT:  Scratch what I stated above... the problem appears to be with the precision difference between a double and a float.

------------------------------------------------------

Alternatively, you can use the C library and a more C++-ish way of doing things:
```

#include <string>
#include <iostream>
#include <iomanip>
#include <cstdlib>

class Converter
{
  public:
    Converter(const std::string& str)
      : m_str(str)
    {
    }

    operator double() const
    {
      return strtod(m_str.c_str(), 0);
    }

    operator float() const
    {
      return strtof(m_str.c_str(), 0);
    }

  private:
    std::string m_str;
};

int main()
{
  Converter conv("147541611");
  double dbl = conv;
  float  flt = conv;

  std::cout << "double value = " << dbl << std::endl;
  std::cout << "float value  = " << flt << std::endl;
  std::cout << "double value = " << std::fixed << dbl << std::endl;  // with these two statements, the
  std::cout << "float value  = " << std::fixed << flt << std::endl;  // problem reappears
}

```

In lieu of strtod() and strtof(), feel free to substitute with the istringstream.

---

