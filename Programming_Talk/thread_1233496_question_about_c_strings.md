---
title: "question about c strings"
date: 2009-08-06
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-08-06
Let's assume that I have this piece of code
[php]int num;
const char* str = new_text.c_str();
if (isdigit(str[0])) num = atoi(str);[/php]


new_text is a std::string. My question is: should I somehow **free** _str_?

---

### Post by Can+~ on 2009-08-06
No. c_str() internally creates that buffer, and as soon as the original string is deleted (or modified, or goes out of scope in case of stack-variable) your str variable will point to an invalid location.

In other words, you should not delete it. (Even [wikipedia]("http://en.wikipedia.org/wiki/String_%28C%2B%2B%29#Operators") agrees)

---

### Post by SledgeHammer_999 on 2009-08-06
ok thank you.

---

### Post by dribeas on 2009-08-06
You can also use pure C++ facilities. You can check boost::lexical_cast, for example. It is a templated method similar to this:

```

namespace imitation {
template <typename R, typename O>
R lexical_cast( O const & value )
{
   std::stringstream st;
   st << value;
   R result;
   st >> result;
   if ( st.fail() ) throw std::bad_cast();
   return result;
}
}
int main( int argc, char** argv )
{
   int value;
   try {
      value = imitation::lexical_cast<int>(argv[1]);
   } catch ( std::bad_cast const & ) {
      std::cout << "Something horrible happened: '" << argv[1] << "' is not an integer" << std::endl;
   }
   std::cout << "argv[1]=" << value << std::endl;
}

```

Now, the real boost version is, of course, better.

---

