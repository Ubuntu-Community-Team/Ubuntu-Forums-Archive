---
title: "Smart pointers"
date: 2010-06-12
forum: Programming Talk
---

### Post by Gunnlaugur on 2010-06-12
Hi.

I'm working on a project in school involving smart pointers.

When I build my project I constantly get this error.

```
Building file: ../src/HLUT4.cpp
Invoking: GCC C++ Compiler
g++ -O0 -g3 -Wall -c -fmessage-length=0 -MMD -MP -MF"src/HLUT4.d" -MT"src/HLUT4.d" -o"src/HLUT4.o" "../src/HLUT4.cpp"
In file included from ../src/HLUT4.cpp:12:
../src/SmartPtrRL.h:25: error: return type specification for constructor invalid
../src/SmartPtrRL.h:25: error: constructors may not be cv-qualified

I haven't implemented my SmartPtrRL.cpp, I'm just getting the skeleton up before I do that.

Here is my code.

My SmartPtrRL.h

#ifndef SMARTPTRRL_H_
#define SMARTPTRRL_H_


template <typename T>
class SmartPtrRL
{
public:
// smiðir
SmartPtrRL();
SmartPtrRL(const SmartPtrRL& rhs);
SmartPtrRL(SmartPtrRL<T>* spr);
~SmartPtrRL();


T* operator->(void) const;
SmartPtrRL& operator = (const SmartPtrRL<T>& rhs) const;
SmartPtrRL<T> SmartPtrRL(T*) const;


/*
SmartPtrRL<T>
SmartPtrRL& operator = (const SmartPtrRL<T>& rhs);
SmartPtrRL* operator -> (skilar T*)
SmartPtrRL<T>
operator -> (skilar T*)
T* operator->() const;
{
*/

private:
T* m_pSmartPtr;
};

#endif /* SMARTPTRRL_H_ */


My SmartPtrRL.cpp so far

#include "SmartPtrRL.h"

SmartPtrRL::SmartPtrRL()
{

}

SmartPtrRL::SmartPtrRL(const SmartPtrRL& rhs)
{

}

SmartPtrRL::SmartPtrRL(SmartPtrRL<T>* spr)
{

}

SmartPtrRL::SmartPtrRL(T*)
{

}

SmartPtrRL::~SmartPtrRL()
{

}

T* SmartPtrRL:perator ->()
{

}


My Date.cpp

#include "Date.h"
#include "stdio.h"

Date:ate()
: m_nYear(0)
, m_nMonth(0)
, m_nDay(0)
{}

Date::~Date()
{
}

Date:ate(int y, int m, int d)
: m_nYear(y)
, m_nMonth(m)
, m_nDay(d)
{
if (m_nMonth < 1
|| m_nMonth > 12)
{
m_nMonth = 0;
}

if (m_nDay < 1
|| m_nDay > 31)
{
m_nDay = 0;
}

if (m_nMonth == 2) // Hér ætti að sjálfsögðu að nota enum eða fasta (const)!
{
if (IsLeapYear())
{
if (m_nDay > 29)
{
m_nDay = 0;
}
}
else
{
if (m_nDay > 2
{
m_nDay = 0;
}
}
}

if (m_nMonth == 4
|| m_nMonth == 6
|| m_nMonth == 9
|| m_nMonth == 11)
{
if (m_nDay > 30)
{
m_nDay = 0;
}
}
}

Date:ate(time_t t)
{
tm* pTm = localtime(&t);

if (pTm != NULL)
{
m_nYear = 1900 + pTm->tm_year;
m_nMonth = 1 + pTm->tm_mon;
m_nDay = pTm->tm_mday;
}
else
{
m_nYear = 0;
m_nMonth = 0;
m_nDay = 0;
}
}

Date:ate(const Date& rhs)
{
printf("Date(const Date& rhs)\n");
m_nYear = rhs.m_nYear;
m_nMonth = rhs.m_nMonth;
m_nDay = rhs.m_nDay;
}

Date& Date:perator = (const Date& rhs)
{
printf("operator = (const Date& rhs)\n");
if (&rhs != this)
{
m_nYear = rhs.m_nYear;
m_nMonth = rhs.m_nMonth;
m_nDay = rhs.m_nDay;
}

return *this;
}

bool Date:perator == (const Date& rhs) const
{
printf("operator == (const Date& rhs) const\n");
return Compare(rhs) == 0;
}

bool Date:perator < (const Date& rhs) const
{
printf("operator < (const Date& rhs) const\n");
return Compare(rhs) < 0;
}

bool Date:perator > (const Date& rhs) const
{
printf("operator > (const Date& rhs) const\n");
return Compare(rhs) > 0;
}

bool Date:perator >= (const Date& rhs) const
{
printf("operator >= (const Date& rhs) const\n");
return Compare(rhs) >= 0;
}

bool Date:perator <= (const Date& rhs) const
{
printf("operator <= (const Date& rhs) const\n");
return Compare(rhs) <= 0;
}

Date Date::Current()
{
printf("Current()\n");
return Date(time(NULL));
}

int Date::Compare(const Date& rhs) const
{
printf("Compare(const Date& rhs) const\n");
if (m_nYear < rhs.m_nYear)
{
return -1;
}
else if (m_nYear > rhs.m_nYear)
{
return 1;
}
else if (m_nMonth < rhs.m_nMonth)
{
return -1;
}
else if (m_nMonth > rhs.m_nMonth)
{
return 1;
}
else if (m_nDay < rhs.m_nDay)
{
return -1;
}
else if (m_nDay > rhs.m_nDay)
{
return 1;
}
return 0;
}

bool Date::IsValid() const
{
if (m_nYear == 0
|| m_nMonth == 0
|| m_nDay == 0)
{
return false;
}

return true;
}

bool Date::IsLeapYear() const
{
if (m_nYear % 400 == 0)
{
return true;
}

if (m_nYear % 100 == 0)
{
return false;
}

if (m_nYear % 4 == 0)
{
return true;
}
return false;
}

int Date::GetYear() const
{
printf("GetYear() const\n");
return m_nYear;
}

int Date::GetMonth() const
{
printf("GetMonth() const\n");
return m_nMonth;
}

int Date::GetDay() const
{
printf("GetDay() const\n");
return m_nDay;
}


My Date.h

#include <time.h>

class Date
{
public:

Date( );
Date( int y, int m, int d );
Date( time_t t );
Date( const Date& rhs );
Date& operator = ( const Date& rhs );
~Date( );

bool operator == ( const Date& rhs ) const;
bool operator < ( const Date& rhs ) const;
bool operator > ( const Date& rhs ) const;
bool operator >= ( const Date& rhs ) const;
bool operator <= ( const Date& rhs ) const;

static Date Current( );

int Compare( const Date& rhs ) const;
bool IsValid( ) const;
bool IsLeapYear( ) const;

int GetYear( ) const;
int GetMonth( ) const;
int GetDay( ) const;

private:

int m_nYear;
int m_nMonth;
int m_nDay;
};


And then my HLUT4.cpp file with main

#include <assert.h>
#include <string>
#include "Date.h"
#include "SmartPtrRL.h"
#include <iostream>
using namespace std;



#ifdef _DEBUG
#define new DEBUG_NEW
#endif

#ifdef _TCHAR
#define new wchar_t
#endif

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


int _tmain( int argc, _TCHAR* argv[] )
{
CreateSmartPointers< Date >( );
CreateSmartPointers< std::string >( );

// Prófum að lokum hvort operator -> virki rétt:
//SmartPtrRL<std::string> ptrString( new std::string( "Nú er gaman" ) );
//assert( ptrString->length( ) == 11 );


return 0;
}
```

Any hints what I'm doing wrong?

Thanks alot

-Gunnlaugur

---

### Post by MadCow108 on 2010-06-12
that is the problem:
SmartPtrRL<T> SmartPtrRL(T*) const;

as the error message tells you, a constructor cannot have a return type and it cannot have a const qualifier
maybe you wanted to overload the () operator?

this is done like this:
return_type operator()(arguments) const {
}

const qualifier is optional

---

### Post by Gunnlaugur on 2010-06-12
> **MadCow108 said:**
> that is the problem:
SmartPtrRL<T> SmartPtrRL(T*) const;

as the error message tells you, a constructor cannot have a return type and it cannot have a const qualifier
maybe you wanted to overload the () operator?

this is done like this:
return_type operator()(arguments) const {
}

const qualifier is optional

Thanks MadCow108 

What I'm supposed to do in my project is,

[LIST]
[*]default constructor
[*]copy constructor
[*]constructor that has T* as input parameter
[*]assignment operator
[*]operator -> that returns T*
[*]operator * that returns T& - reference on to T
[*]destructor
[/LIST]

Thanks 

-Gunnlaugur

---

