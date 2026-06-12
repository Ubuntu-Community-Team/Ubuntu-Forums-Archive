---
title: "[C++] String question"
date: 2010-06-20
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2010-06-20
Is there an easy way to achieve this? Let's say I have 2 strings that start with the same letters but at some point diverge. I want to find that first common part.

Eg 2 strings : **AGFV_265** and **AGFV-8g8g**. I want to get "AGFV". Is there any easy way to get this?

---

### Post by Martin Witte on 2010-06-20
I don't know of a more easy way than
```
$ cat test.cpp 
// string::substr
#include <iostream>
#include <string>
using namespace std;

int main ()
{
  string str1, str2;
  size_t i, len_str2;

  str1="AGFV_265";
  str2="AGFV-8g8g";

  len_str2=str2.length();
  for (i = 0; i< str1.length(); ++i)
  {
      if (i+1 < len_str2)
      {
          if (str1[i] != str2[i])
          {
              break;
          }
      }
  }

  if( i > 0 )
  {
      cout << "Common part of " << str1 << " and " << str2
           << " is " << str1.substr(0, i) << endl;
  }

  return 0;
}

```

when compiled it returns after running:
$ ./a.out 
Common part of AGFV_265 and AGFV-8g8g is AGFV

---

### Post by SledgeHammer_999 on 2010-06-20
I've figured that there isn't an easy way(ie via a convenient function). So I came up with something similar to your:

[php]
#include <string>
#include <iostream>


int main(int argc, char *argv[])
{
    std::string shortest("AGTF_djreie,clg");
    std::string longest("AGTFertert");
    std::string common;
    
    if (longest.size() != shortest.size())
	{
		if (longest.size() < shortest.size()) longest.swap(shortest);
	}

	for (unsigned int i=0; i < shortest.size(); i++)
	{
		if (shortest[i] != longest[i])
		{
			if (i == 0) break; //no common part

			common = shortest.substr(0, i);
			break;
		}
	}
    
    std::cout << "Common is: " << common << std::endl;
    
    return 0;
}[/php]

---

### Post by dwhitney67 on 2010-06-20
> **SledgeHammer_999 said:**
> I've figured that there isn't an easy way(ie via a convenient function). So I came up with something similar to your:


Never mind; I misread your code.  It looks good.

---

### Post by dribeas on 2010-06-22
```

#include <algorithm>
#include <string>
#include <iostream>

// equivalent to end() in STL containers for an array
template <typename T, int N>
inline T* array_end( T (&a)[N] ) {
   return a+N;
}

int main()
{
   const char first[] = "ASDF-1";
   const char second[] = "ASDF-2";

   std::pair<const char*, const char*> res 
      = std::mismatch( first, array_end(first), second );

   std::cout << "Common subsequence has size: " << res.first - first << std::endl;
   std::cout << "\tand value: " << std::string( first, res.first ) << std::endl;
}

```

Mismatch is a common algorithm:

```

template <typename InputIterator1, typename InputIterator2>
std::pair<InputIterator1, InputIterator2> 
mismatch( InputIterator1 first1, InputIterator1 last1, InputIterator2 first2 ) {
  while ( first1!=last1 )  {
    if (*first1 != *first2)
      break;
    ++first1; ++first2;
  }
  return make_pair(first1,first2);
}

```

Note that in the general case it is the responsibility of the caller to verify that the range that starts in 'first2' has at least as many elements as the range [first1,last1), but with C style strings that is not a problem, as there is an extra '\0' at the end, so the algorithm will find a mismatch inside the string always (or will return pointers one beyond the end of both strings if they are the same).

---

