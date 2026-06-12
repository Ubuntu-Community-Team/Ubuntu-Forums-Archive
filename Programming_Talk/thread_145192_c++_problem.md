---
title: "c++ problem"
date: 2006-03-15
forum: Programming Talk
---

### Post by mwanafunzi on 2006-03-15
Hi all,
I am following this tutorial [http://www.ibiblio.org/obp/thinkCS/cpp/english/chap07.htm](http://www.ibiblio.org/obp/thinkCS/cpp/english/chap07.htm). The problem I am having is that when I am not able to use the pstring as has been mentioned in the book. I am getting (in microsoft visual c++) undeclared variable and at home I was getting an error as well. I think it was a variable out of scope. Can anyone help me with this...
Here is sample code

#include <iostream>
using namespace std;
int main()
{
  pstring first;
  first = "Hello, ";
  pstring second = "world."; 
  cout << first << second <<endl;
  return 0;
}

and the error message is 
 error C2065: 'pstring' : undeclared identifier
error C2146: syntax error : missing ';' before identifier 'first'
 error C2065: 'first' : undeclared identifier
 error C2440: '=' : cannot convert from 'char [8]' to 'int'
        This conversion requires a reinterpret_cast, a C-style cast or function-style cast
 error C2146: syntax error : missing ';' before identifier 'second'
 error C2065: 'second' : undeclared identifier
 error C2440: '=' : cannot convert from 'char [7]' to 'int'
        This conversion requires a reinterpret_cast, a C-style cast or function-style cast
Error executing cl.exe.

any suggestions.

---

### Post by hod139 on 2006-03-15
You need to go to this website [http://www.ibiblio.org/obp/pclasses/]("http://www.ibiblio.org/obp/pclasses/")
and download the pstring.h header, which defines the pstring type.  Copy this header to the same location as your source file.  Then at the top of your source file, write
#include "pstring.h"

EDIT:  I should add I found this out by reading the following paragraph in the link you posted 
> The string type we are going to use is called pstring, which is an open-source alternative to a type created specifically for the Computer Science AP Exam. The pclasses, as the entire group of open-source classes are called, can be found in the appendix section of this book. You can also visit their homepage at [http://www.ibiblio.org/obp/pclasses/]("http://www.ibiblio.org/obp/pclasses/").

 If you run across any other p-types you will have to download the appropriate files from that website.

---

### Post by mwanafunzi on 2006-03-15
cheers,
will do that once i get home.

---

### Post by mwanafunzi on 2006-03-20
Hi again,
    I am having some problems, installing pstring.h. What I have done is to copy the file into the same directory as my source file and I added 
#include <pstring.h> in the actual file. I am still getting the same error as before. 
Any ideas as to where I went wrong.

to recap - in my directory I have myfile.cpp and pstring.h
and in myfile.cpp I have #include <pstring.h>


cheers


edit: here is the error message, there seems to be a slight difference.

exFunc.cpp:2:21: error: pstring.h: No such file or directory
exFunc.cpp: In function &#8216;int main()&#8217;:
exFunc.cpp:8: error: &#8216;pstring&#8217; was not declared in this scope
exFunc.cpp:8: error: expected `;' before &#8216;first&#8217;
exFunc.cpp:9: error: &#8216;first&#8217; was not declared in this scope
exFunc.cpp:10: error: expected `;' before &#8216;second&#8217;
exFunc.cpp:11: error: &#8216;second&#8217; was not declared in this scop

---

### Post by zootreeves on 2006-03-20
try #include pstring.h

---

### Post by mwanafunzi on 2006-03-20
Thanks for that suggestion, but it does not work.
I am getting the following error

exFunc.cpp:2:10: error: #include expects "FILENAME" or <FILENAME>

...


edit: an on the side note, here is the code

#include pstring.h
#include <iostream>

using namespace std;

int main()
{
	pstring first;
	first = "hello, ";
	pstring second ="world.";
	cout << first << second << endl;
}

the previous directive was 
#include <pstring.h>

---

### Post by Gustav on 2006-03-20
put "'s around pstring.h

---

### Post by hod139 on 2006-03-20
Look at my first post, I wrote
```
#include "pstring.h"
``` 
"pstring.h" is very different from <pstring.h>. The former tells the preprocessor to look in the current directory for the file. The latter tells it to look in the system directory (usually /usr/include) and any other include directories specified by the flag -I. 

A good rule of thumb is to use "" for files you write, and <> for system includes.

---

### Post by mwanafunzi on 2006-03-20
I neglected to say that i tried the \
#include "pstring.h" 
and the error that I got was this 
pstring.h:75: error: expected initializer before &#8216;&&#8217; token
pstring.h:76: error: expected constructor, destructor, or type conversion before &#8216;&&#8217; token
pstring.h:77: error: expected constructor, destructor, or type conversion before &#8216;&&#8217; token
pstring.h:89: error: expected constructor, destructor, or type conversion before &#8216;&&#8217; token
pstring.h:95: error: expected constructor, destructor, or type conversion before &#8216;&&#8217; token
pstring.h:105: error: expected constructor, destructor, or type conversion before &#8216;&&#8217; token
pstring.h: In member function &#8216;pstringT<T> pstringT<T>::substr(int, int) const&#8217;:
pstring.h:193: error: &#8216;cerr&#8217; was not declared in this scope
pstring.h:194: error: &#8216;endl&#8217; was not declared in this scope
pstring.h: In member function &#8216;T& pstringT<T>::operator[](int)&#8217;:
pstring.h:302: error: &#8216;cerr&#8217; was not declared in this scope
pstring.h:303: error: &#8216;endl&#8217; was not declared in this scope
pstring.h: In member function &#8216;const T pstringT<T>::operator[](int) const&#8217;:
pstring.h:314: error: &#8216;cerr&#8217; was not declared in this scope
pstring.h:315: error: &#8216;endl&#8217; was not declared in this scope
exFunc.cpp: In function &#8216;int main()&#8217;:
exFunc.cpp:12: error: no match for &#8216;operator<<&#8217; in &#8216;std::cout << first&#8217;
/usr/include/c++/4.0.2/bits/ostream.tcc:67: note: candidates are: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>& (*)(std::basic_ostream<_CharT, _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.0.2/bits/ostream.tcc:78: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ios<_CharT, _Traits>& (*)(std::basic_ios<_CharT, _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>]...and it goes on for quite a bit.....

edit: I think i will put down exactly what i did...
I went to the site mentioned above..and did a save link as...saved the file in the same directory as myfile.cpp. 
I have tried the following directives
"pstring.h" <pstring.h> and pstring.h
I hope that i have covered all the steps that I took. 

thanks for the help

---

### Post by hod139 on 2006-03-20
The problem is with pstring.h, not your code. pstring.h isn't using the namespace std. The easiest way to fix the errors is to add 
```

using namespace std; 

``` right after the #includes.

The "better" way would be to not use the "using" keyword, but to add 
```

std::

``` 
in front of each method that is calling a function defined in the std namespace.  For example, line 75 would become
```

**template** <**class** T> **inline** std::ostream & **operator** << (std::ostream &, [COLOR=#800000]const[/COLOR] pstringT<T> &);
```

---

### Post by mwanafunzi on 2006-03-21
Thanks guys for the help.. I (I really can't say I :) ) got it working.

cheers

---

### Post by Roptaty on 2006-03-21
Why not use the std::string class instead of pstring? The class is at least maintained and standard.  After quickly looking through the pstring class I could find one buffer overflow. 

If you have just learning C++, I would strongly encourage you to learn to use classes that are standard in C++ (STL). You can find numerous threads concerning learning C++ in this forum. Thinking in C++, Deitel & Deitel How to program are two fine books. You can find Thinking in C++ for free on the internet. 

Good luck with your programming!

---

