---
title: "Problem with std::string size (C++)"
date: 2011-02-14
forum: Programming Talk
---

### Post by lumulata on 2011-02-14
Hi all this is my first topic and post and only my second day using Linux, so here goes.

I recently installed Ubuntu 10.10 and Im in the process of migrating a C++ console simulation to Ubuntu from Windows.

I have a class with an std::string member variable which is returned by a  getStringMember() method. Now I need to compare this returned value for  equality with the string "Buy".

the code simply looks like this:

std::string returnedString = object.getStringMember();
std::string comparisonString = "Buy";

When returnedString is "Buy" the two strings should be equal, which is  the case in my Windows version. However in Ubuntu and using Code::Blocks  with gcc the returned string has always a size that is one larger than  it ought to. Ive checked that there is no trailing spaces attached.

Does Linux encode std::strings differently and if so what do i need to do for the code to perform as required?

Thanks very much for your time.

---

### Post by Vaphell on 2011-02-14
my very wild guess is that you read data from a text file and windows ignores \r (win files end lines with \r\n) while linux does not (only \n). print out ascii code of the last char in string and see what it is.

---

### Post by lumulata on 2011-02-14
Yep, good guess, to create the string data member i tokenize it from a csv file using boost tokenizer.

In this case is I suppose I should try and remove the \r after creation?

---

### Post by Vaphell on 2011-02-14
internet says that boost offers few nice toys for strings - trim function is what you need.
wikipedia [http://en.wikipedia.org/wiki/Trim_%28programming%29](http://en.wikipedia.org/wiki/Trim_%28programming%29)
> The open source C++ library Boost has several trim variants, including a standard one: [4]
```

#include <boost/algorithm/string/trim.hpp>
trimmed = boost::algorithm::trim_copy("string");
```

Note that with boost's function named simply trim the input sequence is modified in-place[5], and does not return a result.

---

### Post by lumulata on 2011-02-14
Thanks for the guidance, I ended up using 

boost::trim_if(myString, boost::is_any_of("\r"));

---

### Post by forrestcupp on 2011-02-14
Why would you waste resources with a Boost library to trim a string when std::string has its own built-in erase() function and other functions to find a specific string within the string?

---

