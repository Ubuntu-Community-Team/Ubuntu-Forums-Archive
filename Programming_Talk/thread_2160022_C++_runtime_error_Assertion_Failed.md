---
title: "C++ runtime error: Assertion Failed"
date: 2013-07-05
forum: Programming Talk
---

### Post by Dirich on 2013-07-05
Hi, my problem lies with some strange behaviour for which, I guess, the culprit seems to be the mpfr library (arbitrary precision floating point type).
In practice what happens is that if I try to read a value from file when the variable being read is of type mpfr, then it reads one character more than needed (the one at the right of the last character belonging to the number), which does not happen when the variable is of type double.

The code I use to read is the following:

```

inline void Read_New_Line (std::ifstream& reader, std::string& buffer, int& LineNumber)
{
    if (reader.eof ()) {FileHandlingError ReportError (FILE_HANDLING_ERROR___UNEXPECTED_END); throw ReportError;}
    getline (reader, buffer);
    LineNumber++;
    return;
}

template <typename DataType>
inline void Stream_Input (std::istringstream& parser, DataType& data, FileFormatError& ErrorCode)
{
    parser >> data;
    if (parser.fail ()) {ErrorCode.ErrorType = FILE_FORMAT_ERROR___BAD_FORMAT_INPUT; throw ErrorCode;}
    return;
}

```

I use Read_New_Line to load a new line from file into the buffer, then with Stream_Input I read the data (I know how the file is formatted, so I can specify the right type every time I interpret a new set of characters from the buffer).
The program compiles but at runtime, whenever the first character after an (mpfr) number to be read is not a white space, the Stream_Input function throws the exception and stops the normal execution of the program, which tries to write everything it read before ending the run. When trying to read an mpfr variable, even if the exception was not fired when reading it, the program crashes and make gives me the following error message:

```
../../src/get_str.c:153: MPFR assertion failed: size_s1 >= m
make: *** [execute] Aborted (core dumped)
```

As I previously mentioned, when my floating point type is set to double instead of mpfr, there is not this sort of error (using the very same input file), nor the reading problem that forces to use spaces after writing a number.

Any idea of why exactly is this happening? The change of type from double to mpfr should not cause a change in the behaviour of the istringstream operator>>, which is my guess for where the error lies, since the problem is generated at that step.
If it is not a problem of my code, is there any workaround (beside forcing the users to add whitespaces after every number)?



EDIT:
I added the file with the test program. It only needs to be compiled (in the .cpp I wrote the commands I use to compile it). The program writes an input file, reads it and then writes an output file which should be identical to the original input file.
There are 2 macros that you need to play with to check the behaviour:

     if EXTENDED_PRECISION is defined, the program uses mpfr, otherwise it uses double
     if USE_SPACES is defined, the program writes the input file with spaces, otherwise no

The test program runs fine if EXTENDED_PRECISION is not defined, regardless of the other macro.
The test program runs fine if EXTENDED_PRECISION is defined, only if USE_SPACES is defined too. If USE_SPACES is not defined, then every read after the first throws an exception (in the original program the first too threw an exception).

For some reason I am not able to reproduce the other error (the crash of the program when reading a variable that was not properly read, which generates the output from the make command).

---

### Post by dwhitney67 on 2013-07-05
You've inquired about an issue with a software product (MPFR) that may not be commonly used by many developers.  Could you provide some additional details:

1.  What version of the MPFR (C) library are you using?  The latest version is 3.1.2.

2.  Are you using the MPFR C++ library from [http://www.holoborodko.com/pavel/mpfr](http://www.holoborodko.com/pavel/mpfr) or did you make your own?

3.  Can you provide a small, whittled-down, version of your application, and any data file(s), so that other developers can build/test it?

---

### Post by Dirich on 2013-07-05
> **dwhitney67 said:**
> You've inquired about an issue with a software product (MPFR) that may not be commonly used by many developers.  Could you provide some additional details:

1.  What version of the MPFR (C) library are you using?  The latest version is 3.1.2.

2.  Are you using the MPFR C++ library from [http://www.holoborodko.com/pavel/mpfr](http://www.holoborodko.com/pavel/mpfr) or did you make your own?

3.  Can you provide a small, whittled-down, version of your application, and any data file(s), so that other developers can build/test it?

I love enumerated lists too, they make the discussion so much clearer!

1. 3.1.0-p3, the one that was already installed with Ubuntu 12.10. I used the software center to install the -dev, which should only copy mpfr.h to my include folder. I read the version number in the mpfr.h version macro.

2. Yes, I am using mpfr c++, I included the header in the archive with the program you requested in point 3. The only peculiarity is that I modified it with the -pedantic workaround, but, beside for that, it is the latest version in your link.

3. I added an archive with all the necessary files in my first post. I also added an EDIT at the end of such post explaining the macros I defined for testing the problem.

---

### Post by dwhitney67 on 2013-07-05
> **Dirich said:**
> 

     if EXTENDED_PRECISION is defined, the program uses mpfr, otherwise it uses double

Ok... fine.

> **Dirich said:**
> 
     if USE_SPACES is defined, the program writes the input file with spaces, otherwise no

But there are also comma delimiters... why?  Is your data coming from a CSV (Comma Separated Value) file?

Because of the lack of white-space, I would expect that the following method (which is part of the MPFR-C++ library wrapper) will not parse your data correctly.
```

inline std::istream& operator>>(std::istream &is, mpreal& v)
{
    // ToDo, use cout::hexfloat and other flags to setup base
    std::string tmp;
    is >> tmp;
    mpfr_set_str(v.mp, tmp.c_str(), 10, mpreal::get_default_rnd());
    return is;
}

```
The cheesy fix is to ensure that you strip away the commas before attempting to use the operator>> method against an mpreal value.

It's late Friday evening... I'm without beer... and thus my brain is not firing on all cylinders... but here's a crude example:
```

#include "mpreal.h"

#include <string>
#include <sstream>
#include <iostream>

typedef mpfr::mpreal RealType_t;

int main()
{
    std::string input("1.2,1.3,2.6,2.4");

    RealType_t data[4];

    for (int i = 0; i < 4; ++i)
    {
        size_t start = 0;
        size_t comma = input.find_first_of(",");

        std::stringstream iss(input.substr(start, comma - start));    // tokenize the string with the CSV

        iss >> data[i];

        start = comma + 1;
        input = input.substr(start, input.size() - comma);    // advance CSV string

        std::cout << "data[" << i << "] = " << data[i] << std::endl;
    }
}

```

---

