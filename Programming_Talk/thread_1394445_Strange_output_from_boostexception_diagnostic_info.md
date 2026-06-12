---
title: "Strange output from boost::exception diagnostic_information"
date: 2010-01-30
forum: Programming Talk
---

### Post by pholding on 2010-01-30
I've been having a look at the diagnostic_information function in the boost exception library, but seem to be getting a strangely formatted output. 
 
The code I'm using is as follows
```
#include <boost/exception/diagnostic_information.hpp>
#include <stdexcept>
#include <iostream>
void myerror(){
  throw boost::enable_error_info(std::range_error("blah"));
}
int main(){
  try{
    myerror();
  }
  catch(boost::exception & e){
    std::cerr << diagnostic_information(e) << std::endl;
  }
  return 0;
}
```
 
The output is as follows:
> Throw in function (unknown)
Dynamic exception type: N5boost16exception_detail19error_info_injectorISt11range_errorEE
std::exception::what: blah
 
What I don't understand is why I'm getting N5, 16, 19, ISt11 and EE between the details of the exception type. To rule out my code, I compiled the example_io.cpp file provided in the boost example documentation and I'm getting a similar output.
 
Does anyone what is causing the strange characters displayed?
 
I'm running Ubuntu 9.10 and the version of g++ is 4.4.1

---

### Post by dwhitney67 on 2010-01-30
The 5, 16, and 19 seems to imply the number of characters in the error string.  "boost"... 5 characters, "exception_detail"... 19 characters, etc.

As for Boost::exception, I have never used it; and God willing I never will, especially after reading this:
[http://www.boost.org/doc/libs/1_38_0/libs/exception/doc/tutorial_transporting_data.html](http://www.boost.org/doc/libs/1_38_0/libs/exception/doc/tutorial_transporting_data.html)

I cannot think of any possible reason on Earth why I would want to use this feature.  Just because something can be done, it not sufficient justification to actually do it.

Perhaps Dribeas can weigh in with his experience.

---

### Post by pholding on 2010-01-31
Has anyone got any experience of using any other exception libraries for C++. I'm not 100% sure exactly what I'm looking for, other than something that can provide as much detail as possible about what ever exception is thrown. The application I'm developing will use multiple threads. As I'm using several other boost libraries in the app I'm working on, the exception library seemed like something worth looking into, but I'm open to other suggestions.
 
Do most people use the built in exception handling or do they use something else? I've had a look at using return codes but the limited amout of information I can pass back doesn't seem like a good fit.

---

### Post by dwhitney67 on 2010-01-31
I typically use the built-in (that is, the STL) exception classes.  Occasionally I may define my own exception class that extends std::exception.  For example, FileNotFoundException.  For those who program in Java, this exception name might seem familiar.

In other situations, say when I working with a real-time s/w application, the usage of exceptions is not advised.  Thus return codes are used instead.

I'm currently supporting a maintenance contract for "ancient" software applications (written pre-1999) where both exceptions and return values are used.  In many cases, a string object is passed to various functional layers so that error (or success) information can be appended, and ultimately returned to the caller (which typically is a separate process).  I'm not saying this is a "best practice" approach, in fact I dislike it.

As for the Boost exception constructs, first you should determine if you really need something that complex.  I'm sure it is not rocket science to figure out, but I have often times found that simplicity in programming is the best approach, especially if the application will be supported for many years to come.

---

### Post by pholding on 2010-01-31
In case anyone is interested, I posted a message on the boost mailing list and I got a response from author of the library saying that the strange characters are the mangled C++ identifier. He also pointed me in the direction of an article on wikipedia [http://en.wikipedia.org/wiki/Name_mangling#Name_mangling_in_C.2B.2B](http://en.wikipedia.org/wiki/Name_mangling#Name_mangling_in_C.2B.2B)

---

