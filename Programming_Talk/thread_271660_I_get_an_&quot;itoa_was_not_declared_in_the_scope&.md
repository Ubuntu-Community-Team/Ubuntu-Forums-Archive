---
title: "I get an &quot;itoa was not declared in the scope&quot;"
date: 2006-10-05
forum: Programming Talk
---

### Post by thenetduck on 2006-10-05
hey 
 I am trying to convert an int to a string. I'm trying to use the itoa() fucntion but its not working. it gives me the error in the title. Does anyone know what causese this? 
 Thanks, 
 The Net Duck 

 btw its in c++ 

```


string convertToRoman (int number)
{
   // Initialized
   string sNumber;
   itoa(number, sNumber, 10);


```

---

### Post by thumper on 2006-10-05
For C++ avoid using **itoa**.  Preference is to use boost, or failing that, a stringstream.

```
#include <boost/lexical_cast.hpp>

void convert(int number)
{
   std::string val = boost::lexical_cast<std::string>(number);
   // ...
}
```

or

```
#include <sstream>

void convert(int number)
{
   std::istringstream sin;
   sin << number;
   std::string val = sin.str();
   // ...
}
```

---

### Post by thumper on 2006-10-05
As was noted in another post, I got this the wrong way around.

You want an ostringstream not an istringstream.

```
#include <sstream>

void convert(int number)
{
   std::ostringstream sin;
   sin << number;
   std::string val = sin.str();
   // ...
}
```
*blush*

---

