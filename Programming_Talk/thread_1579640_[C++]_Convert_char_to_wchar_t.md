---
title: "[C++] Convert char* to wchar_t"
date: 2010-09-22
forum: Programming Talk
---

### Post by dodle on 2010-09-22
I am trying to convert a char string to a wide char string.

[php]#include <iostream>
using namespace std;

int main(int argc, char* argv[])
{
    if (argc > 1)
        {
        wchar_t* arg1 = (wchar_t*) argv[1];
        cout << arg1 << endl;
        return 0;
    }
    else return 1;
}[/php]

Apart from the above, I have also tried these:
[php]wchar_t* arg1 = argv[1];[/php]
[http://www.cplusplus.com/reference/clibrary/cstdlib/mbstowcs/](http://www.cplusplus.com/reference/clibrary/cstdlib/mbstowcs/)
[php]wchar arg1[512];
mbtowcs(arg1, argv[1], 512);[/php]

I have also seen some suggest using "wcout" instead of cout:
[php]wcout << arg1 << endl;[/php]
but "wcout" isn't found:
```
: error: `wcout' was not declared in this scope
```

---

### Post by dwhitney67 on 2010-09-22
After a few moments of Googling, I found this (partial) solution:
```

#include <locale>
#include <iostream>
#include <string>
#include <sstream>
using namespace std ;

wstring widen( const string& str )
{
    wostringstream wstm ;
    const ctype<wchar_t>& ctfacet = 
                        use_facet< ctype<wchar_t> >( wstm.getloc() ) ;
    for( size_t i=0 ; i<str.size() ; ++i ) 
              wstm << ctfacet.widen( str[i] ) ;
    return wstm.str() ;
}

string narrow( const wstring& str )
{
    ostringstream stm ;
    const ctype<char>& ctfacet = 
                         use_facet< ctype<char> >( stm.getloc() ) ;
    for( size_t i=0 ; i<str.size() ; ++i ) 
                  stm << ctfacet.narrow( str[i], 0 ) ;
    return stm.str() ;
}

int main()
{
  {
    const char* cstr = "abcdefghijkl" ;
    const wchar_t* wcstr = widen(cstr).c_str() ;
    wcout << wcstr << L'\n' ;
  }
  {  
    const wchar_t* wcstr = L"mnopqrstuvwx" ;
    const char* cstr = narrow(wcstr).c_str() ;
    cout << cstr << '\n' ;
  } 
}

```
The only caveat I have found with the code above is that second code-block in the main() function fails to perform its job.  I think it has something to do with the locale used by the ostringstream.

But if all you want is to go from char* to wchar_t*, then just utilize the widen() function, as shown above.

---

### Post by worksofcraft on 2010-09-22
I presume the reason you want to go to wide chars is that you want to use non ascii. For this it is is handy to have a function that can read utf-8 sequences to make a wide char. Do beware though some wide char implementations are apparently not wide enough for unicode so I ended up making my own unicode type.

Someone told me there are standard library routines for converting to and from utf-8 but I had already written my own by then, but just in case you want to have a look anyway I'll attach my source code.

---

### Post by dodle on 2010-09-23
Sorry, I forgot to post that I had found a solution.  I used the C++ function mbstowcs:

[php]#include <iostream>
#include <stdlib.h>
using namespace std;

int main(int argc, char* argv[])
{
    if (argc > 1)
    {
        wchar_t arg1[512];
        mbstowcs(arg1, argv[1], 512);
        wcout << arg1 << endl;
        return 0;
    }
    else return 1;
}[/php]

The reason why I needed to convert to wide char was because I was doing some coding with WINAPI fuctions that required unicode strings.

---

