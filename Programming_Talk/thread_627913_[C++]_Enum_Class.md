---
title: "[C++] Enum Class"
date: 2007-11-30
forum: Programming Talk
---

### Post by iharrold on 2007-11-30
So I am trying to make an intelligent enum, such that if I print an enum value it will translate to a char * and type conversions...

Does this look like the right approach.

framepriority.h
```

#ifndef _FRAMEPRIORITY_H
#define	_FRAMEPRIORITY_H
class frame_priority
{
public:
    frame_priority();
    virtual ~frame_priority(); 
    enum Enum  {normal = 0, hot = 1, hottest = 2 };

    Enum operator=(int i);
    operator int () const;

    Enum operator=(const char* sz);
    bool operator==(const char* sz);
    operator const char* () const;
    
    static Enum AsEnum(const char* sz);
    static Enum AsEnum(int e);
    static const char* AsName(int e);
       
    static bool GetMap(int iIndex, int& iValue, const char*& szDescription);

private:
    Enum m_Enum;

    struct Map_t
    {
        int iValue;
	const char* szDescription;
    };
    static Map_t m_Map[];

    static const int m_iMapSize;
}; 
#endif
```

framepriority.cpp
```
#include "framepriority.h"
#include <string.h>

const int frame_priority::m_iMapSize = 3;

frame_priority::Map_t frame_priority::m_Map[] =
{
    {normal, "NORMAL"},
    {hot,   "HOT"},
    {hottest,  "HOTTEST"}
};

/*----------------------------------------------------------------------------*/
frame_priority::frame_priority()
{
    m_Enum = normal;
}

frame_priority::~frame_priority()
{
}
frame_priority::Enum frame_priority::operator=(int i)
{
    m_Enum = AsEnum(i);
    return m_Enum;
}

frame_priority::operator int () const
{
    return m_Enum;
}

frame_priority::Enum frame_priority::operator=(const char* sz)
{
    m_Enum = AsEnum(sz);
    return m_Enum;    
}

bool frame_priority::operator==(const char* sz)
{
    return m_Enum == AsEnum(sz);
}

frame_priority::operator const char* () const
{
    return AsName(m_Enum);    
}

frame_priority::Enum frame_priority::AsEnum(const char* sz)
{
	for(int i=0;i<m_iMapSize;i++)
	{
		if(strcmp(sz, m_Map[i].szDescription)==0)
		{
			return (frame_priority::Enum)m_Map[i].iValue;
		}
	}
	return (frame_priority::Enum)m_Map[0].iValue;
}  

frame_priority::Enum frame_priority::AsEnum(int e)
{
	for(int i=0;i<m_iMapSize;i++)
	{
		if(m_Map[i].iValue == e)
		{
			return (frame_priority::Enum)m_Map[i].iValue;
		}
	}
	return (frame_priority::Enum)m_Map[0].iValue;
}

const char* frame_priority::AsName(int e)
{
	for(int i=0;i<m_iMapSize;i++)
	{
		if(m_Map[i].iValue == e)
		{
			return m_Map[i].szDescription;
		}
	}
	return m_Map[0].szDescription;
}

bool frame_priority::GetMap(int iIndex, int& iValue, const char*& szDescription)
{
	if(iIndex>=m_iMapSize)
	{
		return false;
	}
	iValue = m_Map[iIndex].iValue;
	szDescription = m_Map[iIndex].szDescription;
	return true;
} 
```

I'm going redo it with an enumeration base class, such that the only thing that would need to be defined is the map, map size and constructor.... and perhaps specialized operators.

---

### Post by aks44 on 2007-11-30
A few tips:

- stop using **int**s where you are supposed to use your **Enum** type. You're just subverting the C++ type system without any gain.

- Class::operator=() returning anything else than Class& is an heresy.

- char* strings are Evil. Come on, it's C++ not C, use std::string.

- ever heard of const correctness?

- why bother with so many (useless IMHO) code when all you need is:
**Enum StringToEnum(const std::string&);** // should throw if the string argument doesn't correspond to any known Enum
**std::string EnumToString(const Enum);** // should throw if the Enum argument is not known (IOW if the library user willingly asked for trouble by casting a random int to Enum)
**bool IsValidEnum(const int);** // you really don't need that one if the two other functions throw

No need for any map, an enum usually contains only very few values so a switch or chained ifs are more than enough.



To sum it up: I don't see the point of such an "intelligent" (???) enum class. IMHO you're wasting your time, just my $0.02.


```
Enum StringToEnum(const std::string& str)
{
  if (str == "NORMAL")
    return normal;
  else if (str == "HOT")
    return hot;
  else if (str == "HOTTEST")
    return hottest;
  else
    throw std::runtime_error("Bad Enum string."); // you may want a specialized exception
}

std::string EnumToString(const Enum val)
{
  switch (val)
  {
  case normal:
    return "NORMAL";
  case hot:
    return "HOT";
  case hottest:
    return "HOTTEST";
  default:
    throw std::runtime_error("Bad Enum value."); // you may want a specialized exception
  };
}
```

---

