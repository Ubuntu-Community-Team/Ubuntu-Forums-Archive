---
title: "multiple errors - error: expected ‘)’ before ‘t’ and more"
date: 2010-06-13
forum: Programming Talk
---

### Post by Gunnlaugur on 2010-06-13
Hello.

I'm working on a project in the university and I have done most of the code but when I try to compile it I keep getting the following errors. I've googled it, but I cant seem to find the exact problem and fix for it.

Any help would be greatly appreciated.

```

**** Build of configuration Debug for project HLUT4 ****

make all 
Building file: ../src/Date.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/Date.d" -MT"src/Date.d" -o"src/Date.o" "../src/Date.cpp"
In file included from ../src/Date.cpp:1:
../src/Date.h:8: error: expected ‘)’ before ‘t’
../src/Date.cpp:44: error: prototype for ‘Date::Date(time_t)’ does not match any in class ‘Date’
../src/Date.h:9: error: candidates are: Date::Date(const Date&)
../src/Date.cpp:14: error:                 Date::Date(int, int, int)
../src/Date.cpp:5: error:                 Date::Date()
../src/Date.cpp: In static member function ‘static Date Date::Current()’:
../src/Date.cpp:103: error: no matching function for call to ‘Date::Date(time_t)’
../src/Date.cpp:58: note: candidates are: Date::Date(const Date&)
../src/Date.cpp:14: note:                 Date::Date(int, int, int)
../src/Date.cpp:5: note:                 Date::Date()
make: *** [src/Date.o] Error 1

```My code:

```

HLUT4.cpp
#include <assert.h>
#include <string>
#include "Date.h"
#include "SmartPtrRL.h"
#include <iostream>
#include <stdlib.h>
//#include "MemLeakTest.h"
using namespace std;



//#ifdef _DEBUG
//#define new DEBUG_NEW
//#endif

template <typename T>
SmartPtrRL<T> UseSmartPtr( SmartPtrRL<T> ptr )
{
    std::cout << *ptr;
    return ptr;
}


template <typename T>
void CreateSmartPointers( )
{
    // Tómur SmartPtrRL á að virka:
    SmartPtrRL<T> emptyPtr;

    // Búum til eina "klíku" með tveim meðlimum:
    SmartPtrRL<T> ptr1( new T( ) );
    SmartPtrRL<T> ptr2 = ptr1;

    // "Assignment to self" ætti að vera noop:
    ptr2 = ptr2;

    // SmartPtrRL ætti að virka bæði sem færibreyta og sem skilagildi:
    SmartPtrRL<T> ptr3 = UseSmartPtr( ptr1 );

    // Búum til aðra SmartPtrRL "klíku":
    SmartPtrRL<T> ptrA( new T( ) );

    SmartPtrRL<T> ptrB( ptrA );
    SmartPtrRL<T> ptrC( ptrA );
    SmartPtrRL<T> ptrD( ptrB );
    SmartPtrRL<T> ptrE( ptrD );

    // látum svo einn skipta um klíku:
    ptrC = ptr2;
}


int main( int argc, char* argv[] )
{
    cout << "bleh" << endl;

    CreateSmartPointers< Date >( );
    CreateSmartPointers< std::string >( );

    // Prófum að lokum hvort operator -> virki rétt:
    SmartPtrRL<std::string> ptrString( new std::string( "Nú er gaman" ) );
    assert( ptrString->length( ) == 11 );


    return 0;
}

Date.h
#include <iosfwd>

class Date {
public:

    Date();
    Date(int y, int m, int d);
    Date(time_t t);
    Date(const Date& rhs);
    Date& operator =(const Date& rhs);
    ~Date();

    bool operator ==(const Date& rhs) const;
    bool operator <(const Date& rhs) const;
    bool operator >(const Date& rhs) const;
    bool operator >=(const Date& rhs) const;
    bool operator <=(const Date& rhs) const;

    static Date Current();

    int Compare(const Date& rhs) const;
    bool IsValid() const;
    bool IsLeapYear() const;

    int GetYear() const;
    int GetMonth() const;
    int GetDay() const;

private:

    int m_nYear;
    int m_nMonth;
    int m_nDay;
};
std::ostream& operator <<(std::ostream& lhs, const Date& rhs);

Note: I get these errors in Date.h
"expected ‘)’ before ‘t’" on this decloration Date(time_t t);
and this forDate(const Date&) I get "candidates are: Date::Date(const Date&)"

Date.cpp
#include "Date.h"
#include "stdio.h"
#include <ostream>

Date::Date() {
    m_nYear = 0;
    m_nMonth = 0;
    m_nDay = 0;
}

Date::~Date() {
}

Date::Date(int y, int m, int d) :
    m_nYear(y), m_nMonth(m), m_nDay(d) {
    if (m_nMonth < 1 || m_nMonth > 12) {
        m_nMonth = 0;
    }

    if (m_nDay < 1 || m_nDay > 31) {
        m_nDay = 0;
    }

    if (m_nMonth == 2) // Hér ætti að sjálfsögðu að nota enum eða fasta (const)!
    {
        if (IsLeapYear()) {
            if (m_nDay > 29) {
                m_nDay = 0;
            }
        } else {
            if (m_nDay > 28) {
                m_nDay = 0;
            }
        }
    }

    if (m_nMonth == 4 || m_nMonth == 6 || m_nMonth == 9 || m_nMonth == 11) {
        if (m_nDay > 30) {
            m_nDay = 0;
        }
    }
}

Date::Date(time_t t) {
    tm* pTm = localtime(&t);

    if (pTm != NULL) {
        m_nYear = 1900 + pTm->tm_year;
        m_nMonth = 1 + pTm->tm_mon;
        m_nDay = pTm->tm_mday;
    } else {
        m_nYear = 0;
        m_nMonth = 0;
        m_nDay = 0;
    }
}

Date::Date(const Date& rhs) {
    printf("Date(const Date& rhs)\n");
    m_nYear = rhs.m_nYear;
    m_nMonth = rhs.m_nMonth;
    m_nDay = rhs.m_nDay;
}

Date& Date::operator =(const Date& rhs) {
    printf("operator = (const Date& rhs)\n");
    if (&rhs != this) {
        m_nYear = rhs.m_nYear;
        m_nMonth = rhs.m_nMonth;
        m_nDay = rhs.m_nDay;
    }

    return *this;
}

bool Date::operator ==(const Date& rhs) const {
    printf("operator == (const Date& rhs) const\n");
    return Compare(rhs) == 0;
}

bool Date::operator <(const Date& rhs) const {
    printf("operator < (const Date& rhs) const\n");
    return Compare(rhs) < 0;
}

bool Date::operator >(const Date& rhs) const {
    printf("operator > (const Date& rhs) const\n");
    return Compare(rhs) > 0;
}

bool Date::operator >=(const Date& rhs) const {
    printf("operator >= (const Date& rhs) const\n");
    return Compare(rhs) >= 0;
}

bool Date::operator <=(const Date& rhs) const {
    printf("operator <= (const Date& rhs) const\n");
    return Compare(rhs) <= 0;
}

Date Date::Current() {
    printf("Current()\n");
    return Date(time(NULL));
}

int Date::Compare(const Date& rhs) const {
    printf("Compare(const Date& rhs) const\n");
    if (m_nYear < rhs.m_nYear) {
        return -1;
    } else if (m_nYear > rhs.m_nYear) {
        return 1;
    } else if (m_nMonth < rhs.m_nMonth) {
        return -1;
    } else if (m_nMonth > rhs.m_nMonth) {
        return 1;
    } else if (m_nDay < rhs.m_nDay) {
        return -1;
    } else if (m_nDay > rhs.m_nDay) {
        return 1;
    }
    return 0;
}

bool Date::IsValid() const {
    if (m_nYear == 0 || m_nMonth == 0 || m_nDay == 0) {
        return false;
    }

    return true;
}

bool Date::IsLeapYear() const {
    if (m_nYear % 400 == 0) {
        return true;
    }

    if (m_nYear % 100 == 0) {
        return false;
    }

    if (m_nYear % 4 == 0) {
        return true;
    }
    return false;
}

int Date::GetYear() const {
    printf("GetYear() const\n");
    return m_nYear;
}

int Date::GetMonth() const {
    printf("GetMonth() const\n");
    return m_nMonth;
}

int Date::GetDay() const {
    printf("GetDay() const\n");
    return m_nDay;
}

std::ostream& operator <<(std::ostream& lhs, const Date& rhs) {
    lhs.fill('0');
    lhs.width('2');
    lhs << rhs.GetYear() << "-" << rhs.GetMonth() << "-" << rhs.GetDay();
    return lhs;
}

Note: I get these errors in Date.cpp
                Date::Date()
                Date::Date(int, int, int)
prototype for ‘Date::Date(time_t)’ does not match any in class ‘Date’
no matching function for call to ‘Date::Date(time_t)’ on this "return Date(time(NULL));" in Date Date::Current()

And then my SmartPtrRL.h
/*
 * SmartPtrRL.h
 *
 *  Created on: Jun 11, 2010
 *      Author: gunnl
 */

#ifndef SMARTPTRRL_H_
#define SMARTPTRRL_H_

#include <string>
#include <iostream>

using namespace std;

template<typename T>
class SmartPtrRL {
public:
    /* constructors */
    SmartPtrRL();
    SmartPtrRL(SmartPtrRL<T>& rhs);
    SmartPtrRL(T* ptr);

    /* destructor */
    ~SmartPtrRL();

    /* operators */
    T* operator->();
    T& operator*();
    SmartPtrRL<T>& operator =(SmartPtrRL<T>& rhs);

private:
    T* _pointee;
    SmartPtrRL* _next;
    SmartPtrRL* _prev;
};

template<class T>
SmartPtrRL<T>::SmartPtrRL() {
    _pointee = NULL;
    _next = NULL;
    _prev = NULL;
}

template<typename T>
SmartPtrRL<T>::SmartPtrRL(SmartPtrRL<T>& rhs) {
    _pointee = rhs._pointee;
    _prev = &rhs;
    _next = NULL;
    rhs._next = this;
}

template<typename T>
SmartPtrRL<T>::SmartPtrRL(T* ptr) {
    _pointee = ptr;
    _next = NULL;
    _prev = NULL;
}

template<typename T>
SmartPtrRL<T>::~SmartPtrRL() {
    // smart pointerinn bendir ekki lengur á neitt, því óhætt að eyða pointernum
    if ((_next == NULL) && (_prev == NULL)) {
        delete _pointee;
    } else { // annars verður að láta fyrri benda á næsta pointer þar á eftir
        _prev->_next = _next;
        // og svo ef pointerinn næsta á þá verður að
        if (_next != NULL) {
            _next->_prev = _prev;
        }
    }
}

template<typename T>
T& SmartPtrRL<T>::operator*() {
    return *_pointee;
}

template<typename T>
T* SmartPtrRL<T>::operator->() {
    return _pointee;
}

// glæra 15 í pakka 10 - reference linking
template<typename T>
SmartPtrRL<T>& SmartPtrRL<T>::operator =(SmartPtrRL<T>& rhs) {
    // ef þetta tilvik og það sem er hægra megin eru ekki sama tilvikið þá
    // þurfum við að láta this taka gildi af rhs annars skilum við þessu tilviki
    if (this != &rhs) {
        // smart pointerinn bendir ekki lengur á neitt, því óhætt að eyða pointernum
        if (_next == NULL && _prev == NULL) {
            delete _pointee;
        } else { // annars verður að láta fyrri benda á næsta pointer þar á eftir
            rhs._prev->_next = _next;
            if (_next != NULL) { // og svo tengja pointernum inn í keðjuna
                rhs._next->_prev = _prev;
            }
        }
        _pointee = rhs._pointee;
        _prev = &rhs;
        _next = NULL;
        rhs._next = this;
    }
    return *this;
}

#endif /* SMARTPTRRL_H_ */

```Thanks

-Gunnlaugur

---

### Post by ju2wheels on 2010-06-13
1. Remove the function prototype for operator << from the end of Date.h

2. Either append the right namespace (ill assume std) to time_t and make it std::time_t where ever you use that type or just add "using namespace std;" after your includes in Date.h

3. In Date.cpp, unless there is particular reason, for which I cant think of one right now, change #include "stdio.h" to #include <cstdio>

4. In Date.cpp, again you forgot to specify namespace, so either add using namespace std after your includes or append std:: to variable types that originate from included libraries.

There may be more errors but that should at least give you a start.

[Edit]

5. In your main file change these:
#include <assert.h>
#include <stdlib.h> 

to these:

#include <cassert>
#include <cstdlib>

(If you dont understand that please ask your professor to properly explain how standard C libraries should be included in C++)

---

### Post by Gunnlaugur on 2010-06-14
Thanks ju2wheels.

I followed your advice and it cleard my some of my previous errors but now I get new ones.

Date.cpp now has this at the top
```

#include <cstdio>
#include <ostream>
#include "Date.h"

using namespace std;

```And my HLUT4.cpp now looks like this at the top
```

#include <string>
#include "Date.h"
#include "SmartPtrRL.h"
#include <iostream>
#include <cassert>
#include <cstdlib>
//#include "MemLeakTest.h"

using namespace std;

```But then again, if I remove the function prototype for operator << from the end of Date.h I get an when I compile.

```

**** Build of configuration Debug for project HLUT4 ****

make all 
Building file: ../src/Date.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/Date.d" -MT"src/Date.d" -o"src/Date.o" "../src/Date.cpp"
Finished building: ../src/Date.cpp
 
Building file: ../src/HLUT4.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/HLUT4.d" -MT"src/HLUT4.d" -o"src/HLUT4.o" "../src/HLUT4.cpp"
../src/HLUT4.cpp: In function ‘void CreateSmartPointers() [with T = Date]’:
../src/HLUT4.cpp:57:   instantiated from here
../src/HLUT4.cpp:38: error: no matching function for call to ‘SmartPtrRL<Date>::SmartPtrRL(SmartPtrRL<Date>)’
../src/SmartPtrRL.h:54: note: candidates are: SmartPtrRL<T>::SmartPtrRL(T*) [with T = Date]
../src/SmartPtrRL.h:46: note:                 SmartPtrRL<T>::SmartPtrRL(SmartPtrRL<T>&) [with T = Date]
../src/SmartPtrRL.h:39: note:                 SmartPtrRL<T>::SmartPtrRL() [with T = Date]
../src/HLUT4.cpp: In function ‘void CreateSmartPointers() [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]’:
../src/HLUT4.cpp:58:   instantiated from here
../src/HLUT4.cpp:38: error: no matching function for call to ‘SmartPtrRL<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::SmartPtrRL(SmartPtrRL<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >)’
../src/SmartPtrRL.h:54: note: candidates are: SmartPtrRL<T>::SmartPtrRL(T*) [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
../src/SmartPtrRL.h:46: note:                 SmartPtrRL<T>::SmartPtrRL(SmartPtrRL<T>&) [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
../src/SmartPtrRL.h:39: note:                 SmartPtrRL<T>::SmartPtrRL() [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
../src/HLUT4.cpp: In function ‘SmartPtrRL<T> UseSmartPtr(SmartPtrRL<T>) [with T = Date]’:
../src/HLUT4.cpp:38:   instantiated from ‘void CreateSmartPointers() [with T = Date]’
../src/HLUT4.cpp:57:   instantiated from here
../src/HLUT4.cpp:19: error: no match for ‘operator<<’ in ‘std::cout << ptr.SmartPtrRL<T>::operator* [with T = Date]()’
/usr/include/c++/4.4/ostream:108: note: candidates are: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>& (*)(std::basic_ostream<_CharT, _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:117: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ios<_CharT, _Traits>& (*)(std::basic_ios<_CharT, _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:127: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::ios_base& (*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:165: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:169: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:173: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(bool) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/bits/ostream.tcc:91: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:180: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short unsigned int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/bits/ostream.tcc:105: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:191: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(unsigned int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:200: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long long int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:204: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:209: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:213: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(float) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:221: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long double) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/ostream:225: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(const void*) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.4/bits/ostream.tcc:119: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_streambuf<_CharT, _Traits>*) [with _CharT = char, _Traits = std::char_traits<char>]
make: *** [src/HLUT4.o] Error 1

```But then if I keep the function prototype in Date.h I get the the following error

```

**** Build of configuration Debug for project HLUT4 ****

make all 
Building file: ../src/Date.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/Date.d" -MT"src/Date.d" -o"src/Date.o" "../src/Date.cpp"
Finished building: ../src/Date.cpp
 
Building file: ../src/HLUT4.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/HLUT4.d" -MT"src/HLUT4.d" -o"src/HLUT4.o" "../src/HLUT4.cpp"
../src/HLUT4.cpp: In function ‘void CreateSmartPointers() [with T = Date]’:
../src/HLUT4.cpp:57:   instantiated from here
../src/HLUT4.cpp:38: error: no matching function for call to ‘SmartPtrRL<Date>::SmartPtrRL(SmartPtrRL<Date>)’
../src/SmartPtrRL.h:54: note: candidates are: SmartPtrRL<T>::SmartPtrRL(T*) [with T = Date]
../src/SmartPtrRL.h:46: note:                 SmartPtrRL<T>::SmartPtrRL(SmartPtrRL<T>&) [with T = Date]
../src/SmartPtrRL.h:39: note:                 SmartPtrRL<T>::SmartPtrRL() [with T = Date]
../src/HLUT4.cpp: In function ‘void CreateSmartPointers() [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]’:
../src/HLUT4.cpp:58:   instantiated from here
../src/HLUT4.cpp:38: error: no matching function for call to ‘SmartPtrRL<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::SmartPtrRL(SmartPtrRL<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >)’
../src/SmartPtrRL.h:54: note: candidates are: SmartPtrRL<T>::SmartPtrRL(T*) [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
../src/SmartPtrRL.h:46: note:                 SmartPtrRL<T>::SmartPtrRL(SmartPtrRL<T>&) [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
../src/SmartPtrRL.h:39: note:                 SmartPtrRL<T>::SmartPtrRL() [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
make: *** [src/HLUT4.o] Error 1

```And in my HLUT4.cpp this line has an error 

```

SmartPtrRL<T> ptr3 = UseSmartPtr( ptr1 );

```Any hint why I get these errors?

Thanks

-Gunnlaugur

---

### Post by dwhitney67 on 2010-06-14
Your UseSmartPtr() function has an interesting signature which is causing the compiler issue.

Here's is _some_ of your code in a state in which it will compile:
```

**#include <ctime>**   // this is where time_t is defined!
#include <iosfwd>

class Date
{
public:
   Date() : _time(0) {}
   Date(time_t theTime) : _time(theTime) {}
   Date(const Date& other) : _time(other._time) {}

   **friend std::ostream& operator<<(std::ostream& os, const Date& date);**

private:
   time_t _time;
};

std::ostream& operator<<(std::ostream& os, const Date& date)
{
   os << date._time;
   return os;
}


template <typename T>
class SmartPtrRL
{
public:
   SmartPtrRL() : _pointee(0), _prev(0), _next(0) {}
   SmartPtrRL(SmartPtrRL<T>& other) : _pointee(other._pointee), _prev(&other), _next(0) {}
   SmartPtrRL(T* ptr) : _pointee(ptr), _prev(0), _next(0) {}

   ~SmartPtrRL()
   {
      // smart pointerinn bendir ekki lengur á neitt, því óhætt að eyða pointernum
      if ((_next == NULL) && (_prev == NULL))
      {
         delete _pointee;
      }
      else // annars verður að láta fyrri benda á næsta pointer þar á eftir
      {
         _prev->_next = _next;
         // og svo ef pointerinn næsta á þá verður að
         if (_next != NULL)
         {
            _next->_prev = _prev;
         }
      }
   }

   SmartPtrRL<T>& operator=(SmartPtrRL<T>& rhs)
   {
      // ef þetta tilvik og það sem er hægra megin eru ekki sama tilvikið þá
      // þurfum við að láta this taka gildi af rhs annars skilum við þessu tilviki
      if (this != &rhs)
      {
         // smart pointerinn bendir ekki lengur á neitt, því óhætt að eyða pointernum
         if (_next == NULL && _prev == NULL)
         {
            delete _pointee;
         }
         else // annars verður að láta fyrri benda á næsta pointer þar á eftir
         {
            rhs._prev->_next = _next;
            if (_next != NULL) // og svo tengja pointernum inn í keðjuna
            {
               rhs._next->_prev = _prev;
            }
         }
         _pointee = rhs._pointee;
         _prev = &rhs;
         _next = NULL;
         rhs._next = this;
      }

      return *this;
   }

   T& operator*()  { return *_pointee; }
   T* operator->() { return _pointee; }

private:
   T*          _pointee;
   SmartPtrRL* _prev;
   SmartPtrRL* _next;
};


template <typename T>
**SmartPtrRL<T>& useSmartPtr(SmartPtrRL<T>& ptr)**
{
   return ptr;
}


template <typename T>
void createPointers()
{
   SmartPtrRL<T> emptyPtr;

   SmartPtrRL<T> ptr1(new T());
   SmartPtrRL<T> ptr2 = ptr1;

   ptr2 = ptr2;

   SmartPtrRL<T> ptr3 = useSmartPtr(ptr1);

   SmartPtrRL<T> ptrA(new T());

   SmartPtrRL<T> ptrB(ptrA);
   SmartPtrRL<T> ptrC(ptrA);
   SmartPtrRL<T> ptrD(ptrB);
   SmartPtrRL<T> ptrE(ptrD);

   ptrC = ptr2;
}


int main()
{
   createPointers<Date>();
}

```
The main things to notice is:

1.  "time_t" is defined in <ctime>

2.  The operator<<() method you had is ok, however it is better to define it as a friend of class Date so that it can have access to the private member data.

3.  The signature of useSmartPtr().


P.S.  Everybody seems to have their own programming style; mine is demonstrated above.

---

### Post by Gunnlaugur on 2010-06-16
Thanks dwhitney67
  
I flollowd many of your advice. But I left HLUT4.cpp mostly unchanged, since it is provided by my professor and it must pass it.

But this is what my code looks now.

Date.h
```

#include <ctime>
#include <iosfwd>
#include <iostream>

class Date {
public:

    Date();
    Date(int y, int m, int d);
    Date(time_t t);
    Date(const Date& rhs);
    ~Date();

    Date& operator =(const Date& rhs);
    bool operator ==(const Date& rhs) const;
    bool operator <(const Date& rhs) const;
    bool operator >(const Date& rhs) const;
    bool operator >=(const Date& rhs) const;
    bool operator <=(const Date& rhs) const;

    static Date Current();

    int Compare(const Date& rhs) const;
    bool IsValid() const;
    bool IsLeapYear() const;

    int GetYear() const;
    int GetMonth() const;
    int GetDay() const;

    friend std::ostream& operator <<(std::ostream& lhs, const Date& rhs);

private:
//    time_t _time;

    int m_nYear;
    int m_nMonth;
    int m_nDay;
};


std::ostream& operator <<(std::ostream& lhs, const Date& rhs) {
    lhs << rhs.GetYear() << "-" << rhs.GetMonth() << "-" << rhs.GetDay();
    return lhs;
}

```Date.cpp
```

#include <cstdio>
#include <ostream>
#include <ctime>
#include "Date.h"

using namespace std;

Date::Date() {
    m_nYear = 0;
    m_nMonth = 0;
    m_nDay = 0;
}

Date::~Date() {
}

Date::Date(int y, int m, int d) :
//Date::Date(time_t theTime) : _time(theTime) {

    m_nYear(y), m_nMonth(m), m_nDay(d) {


    if (m_nMonth < 1 || m_nMonth > 12) {
        m_nMonth = 0;
    }

    if (m_nDay < 1 || m_nDay > 31) {
        m_nDay = 0;
    }

    if (m_nMonth == 2) // Hér ætti að sjálfsögðu að nota enum eða fasta (const)!
    {
        if (IsLeapYear()) {
            if (m_nDay > 29) {
                m_nDay = 0;
            }
        } else {
            if (m_nDay > 28) {
                m_nDay = 0;
            }
        }
    }

    if (m_nMonth == 4 || m_nMonth == 6 || m_nMonth == 9 || m_nMonth == 11) {
        if (m_nDay > 30) {
            m_nDay = 0;
        }
    }
}

Date::Date(time_t t) {
    tm* pTm = localtime(&t);

    if (pTm != NULL) {
        m_nYear = 1900 + pTm->tm_year;
        m_nMonth = 1 + pTm->tm_mon;
        m_nDay = pTm->tm_mday;
    } else {
        m_nYear = 0;
        m_nMonth = 0;
        m_nDay = 0;
    }
}

Date::Date(const Date& rhs) {
    printf("Date(const Date& rhs)\n");
    m_nYear = rhs.m_nYear;
    m_nMonth = rhs.m_nMonth;
    m_nDay = rhs.m_nDay;
}

Date& Date::operator =(const Date& rhs) {
    printf("operator = (const Date& rhs)\n");
    if (&rhs != this) {
        m_nYear = rhs.m_nYear;
        m_nMonth = rhs.m_nMonth;
        m_nDay = rhs.m_nDay;
    }

    return *this;
}

bool Date::operator ==(const Date& rhs) const {
    printf("operator == (const Date& rhs) const\n");
    return Compare(rhs) == 0;
}

bool Date::operator <(const Date& rhs) const {
    printf("operator < (const Date& rhs) const\n");
    return Compare(rhs) < 0;
}

bool Date::operator >(const Date& rhs) const {
    printf("operator > (const Date& rhs) const\n");
    return Compare(rhs) > 0;
}

bool Date::operator >=(const Date& rhs) const {
    printf("operator >= (const Date& rhs) const\n");
    return Compare(rhs) >= 0;
}

bool Date::operator <=(const Date& rhs) const {
    printf("operator <= (const Date& rhs) const\n");
    return Compare(rhs) <= 0;
}

Date Date::Current() {
    printf("Current()\n");
    return Date(time(NULL));
}

int Date::Compare(const Date& rhs) const {
    printf("Compare(const Date& rhs) const\n");
    if (m_nYear < rhs.m_nYear) {
        return -1;
    } else if (m_nYear > rhs.m_nYear) {
        return 1;
    } else if (m_nMonth < rhs.m_nMonth) {
        return -1;
    } else if (m_nMonth > rhs.m_nMonth) {
        return 1;
    } else if (m_nDay < rhs.m_nDay) {
        return -1;
    } else if (m_nDay > rhs.m_nDay) {
        return 1;
    }
    return 0;
}

bool Date::IsValid() const {
    if (m_nYear == 0 || m_nMonth == 0 || m_nDay == 0) {
        return false;
    }

    return true;
}

bool Date::IsLeapYear() const {
    if (m_nYear % 400 == 0) {
        return true;
    }

    if (m_nYear % 100 == 0) {
        return false;
    }

    if (m_nYear % 4 == 0) {
        return true;
    }
    return false;
}

int Date::GetYear() const {
    printf("GetYear() const\n");
    return m_nYear;
}

int Date::GetMonth() const {
    printf("GetMonth() const\n");
    return m_nMonth;
}

int Date::GetDay() const {
    printf("GetDay() const\n");
    return m_nDay;
}

```ShartPtrRL.h
```

/*
 * SmartPtrRL.h
 *
 *  Created on: Jun 11, 2010
 *      Author: gunnl
 */

#ifndef SMARTPTRRL_H_
#define SMARTPTRRL_H_

#include <string>
#include <iostream>

using namespace std;

/* Ég útfæri öll föllin inline */
template<typename T>
class SmartPtrRL {
public:

    /* constructors */
    SmartPtrRL() {
        _pointee = NULL;
        _prev = NULL;
        _next = NULL;
    }
    SmartPtrRL(SmartPtrRL<T>& other) {
        _pointee = other._pointee;
        _prev = &other;
        _next = NULL;
    }
    SmartPtrRL(T* ptr) {
        _pointee = ptr;
        _prev = NULL;
        _next= NULL;
    }

    /* destructor */
    ~SmartPtrRL() {
        // smart pointerinn bendir ekki lengur á neitt, því óhætt að eyða pointernum
        if ((_next == NULL) && (_prev == NULL)) {
            delete _pointee;
        } else // annars verður að láta fyrri benda á næsta pointer þar á eftir
        {
            _prev->_next = _next;
            // og svo ef pointerinn næsta á þá verður að
            if (_next != NULL) {
                _next->_prev = _prev;
            }
        }
    }

    /* operators */
    SmartPtrRL<T>& operator=(SmartPtrRL<T>& rhs) {
        // ef þetta tilvik og það sem er hægra megin eru ekki sama tilvikið þá
        // þurfum við að láta this taka gildi af rhs annars skilum við þessu tilviki
        if (this != &rhs) {
            // smart pointerinn bendir ekki lengur á neitt, því óhætt að eyða pointernum
            if (_next == NULL && _prev == NULL) {
                delete _pointee;
            } else // annars verður að láta fyrri benda á næsta pointer þar á eftir
            {
                rhs._prev->_next = _next;
                if (_next != NULL) // og svo tengja pointernum inn í keðjuna
                {
                    rhs._next->_prev = _prev;
                }
            }
            _pointee = rhs._pointee;
            _prev = &rhs;
            _next = NULL;
            rhs._next = this;
        }
        return *this;
    }

    T& operator*() {
        return *_pointee;
    }
    T* operator->() {
        return _pointee;
    }

private:
    T* _pointee;
    SmartPtrRL* _prev;
    SmartPtrRL* _next;
};

#endif /* SMARTPTRRL_H_ */

```Then my HLUT4.cpp
```

#include <string>
#include "Date.h"
#include "SmartPtrRL.h"
#include <iostream>
#include <cassert>
#include <cstdlib>
//#include "MemLeakTest.h"
using namespace std;



//#ifdef _DEBUG
//#define new DEBUG_NEW
//#endif

template <typename T>
SmartPtrRL<T> UseSmartPtr( SmartPtrRL<T> ptr )
{
    std::cout << *ptr;
    return ptr;
}


template <typename T>
void CreateSmartPointers( )
{
    // Tómur SmartPtrRL á að virka:
    SmartPtrRL<T> emptyPtr;

    // Búum til eina "klíku" með tveim meðlimum:
    SmartPtrRL<T> ptr1( new T( ) );
    SmartPtrRL<T> ptr2 = ptr1;

    // "Assignment to self" ætti að vera noop:
    ptr2 = ptr2;

    // SmartPtrRL ætti að virka bæði sem færibreyta og sem skilagildi:
    SmartPtrRL<T> ptr3 = UseSmartPtr<T>( ptr1 );

    // Búum til aðra SmartPtrRL "klíku":
    SmartPtrRL<T> ptrA( new T( ) );

    SmartPtrRL<T> ptrB( ptrA );
    SmartPtrRL<T> ptrC( ptrA );
    SmartPtrRL<T> ptrD( ptrB );
    SmartPtrRL<T> ptrE( ptrD );

    // látum svo einn skipta um klíku:
    ptrC = ptr2;
}


int main( int argc, char* argv[] )
{
    cout << "bleh" << endl;

    CreateSmartPointers< Date >( );
    CreateSmartPointers< std::string >( );

    // Prófum að lokum hvort operator -> virki rétt:
    SmartPtrRL<std::string> ptrString( new std::string( "Nú er gaman" ) );
    assert( ptrString->length( ) == 11 );


    return 0;
}

```But the line 38 is giving me error in HLUT4.cpp is the following
```

SmartPtrRL<T> ptr3 = UseSmartPtr<T>( ptr1 );

```And the error I'm getting is the following.
```

**** Build of configuration Debug for project HLUT4 ****

make all 
Building file: ../src/Date.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/Date.d" -MT"src/Date.d" -o"src/Date.o" "../src/Date.cpp"
Finished building: ../src/Date.cpp
 
Building file: ../src/HLUT4.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/HLUT4.d" -MT"src/HLUT4.d" -o"src/HLUT4.o" "../src/HLUT4.cpp"
../src/HLUT4.cpp: In function ‘void CreateSmartPointers() [with T = Date]’:
../src/HLUT4.cpp:57:   instantiated from here
../src/HLUT4.cpp:38: error: no matching function for call to ‘SmartPtrRL<Date>::SmartPtrRL(SmartPtrRL<Date>)’
../src/SmartPtrRL.h:32: note: candidates are: SmartPtrRL<T>::SmartPtrRL(T*) [with T = Date]
../src/SmartPtrRL.h:27: note:                 SmartPtrRL<T>::SmartPtrRL(SmartPtrRL<T>&) [with T = Date]
../src/SmartPtrRL.h:22: note:                 SmartPtrRL<T>::SmartPtrRL() [with T = Date]
../src/HLUT4.cpp: In function ‘void CreateSmartPointers() [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]’:
../src/HLUT4.cpp:58:   instantiated from here
../src/HLUT4.cpp:38: error: no matching function for call to ‘SmartPtrRL<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::SmartPtrRL(SmartPtrRL<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >)’
../src/SmartPtrRL.h:32: note: candidates are: SmartPtrRL<T>::SmartPtrRL(T*) [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
../src/SmartPtrRL.h:27: note:                 SmartPtrRL<T>::SmartPtrRL(SmartPtrRL<T>&) [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
../src/SmartPtrRL.h:22: note:                 SmartPtrRL<T>::SmartPtrRL() [with T = std::basic_string<char, std::char_traits<char>, std::allocator<char> >]
make: *** [src/HLUT4.o] Error 1

```Any other hints or advice ?

Thanks 

-Gunnlaugur

---

### Post by Gunnlaugur on 2010-06-16
I was able to fix the problem with a litle help from my professor.

The fix was to make the smart pointer input const.
```

    SmartPtrRL(const SmartPtrRL<T>& other) {
        _pointee = other._pointee;
        _prev = &const_cast< SmartPtrRL<T>& >( other );
        _next = NULL;
    }

```And then make private members mutable.
```

mutable SmartPtrRL* _prev;
mutable SmartPtrRL* _next;

```I like to thank you all for the help you provided 

Cheers
-Gunnlaugur

---

### Post by ju2wheels on 2010-06-16
Looks like copy constructor funkiness to me [http://en.wikipedia.org/wiki/Copy_constructor](http://en.wikipedia.org/wiki/Copy_constructor) .

[Edit] ehhh  you beat me to it. Happy coding...

---

