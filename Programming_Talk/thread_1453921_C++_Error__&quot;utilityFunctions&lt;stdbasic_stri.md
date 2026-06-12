---
title: "C++ Error:  &quot;utilityFunctions&lt;std::basic_string&lt;char,...)&quot; , referenced from:"
date: 2010-04-13
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-04-13
Ey guys, so I moved some functions from my main.cpp into separate files and am now getting a bunch of errors that look like this(I will present you one of the errors and hopefully if I figure out the problem to this I can figure it out for the rest):
```

  "utilityFunctions<std::basic_string<char, std::char_traits<char>, std::allocator<char> > >::isInStr(char, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)", referenced from:
           isSpecialChar(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)in ebnfFunctions.o
           properNum(std::basic_string<char, std::char_traits<char>, std::allocator<char> >)in ebnfFunctions.o

```
And here are the relevant portions of my code:
```

//ebnfFunctions.h
#ifndef ebnfFunctions_h
#define ebnfFunctions_h

#include <vector>
#include <string>
#include "lineManager.h"
#include "utilityFunctions.h"

class lineManager;

class ebnfFunctions{
public:
	static long charTypeAstrkBegCmnt(std::string line, std::vector<std::string> vectLine);
	static long charTypeAstrkEndCmnt(std::string line, std::vector<std::string> vectLine);
	static long charTypeFSCmnt(std::string line, std::vector<std::string> vectLine);
	static bool isSpecialChar(std::string varInQuestion);
	static bool properNum(std::string var);
	static bool properVar(std::string var);
	static bool appropVal(std::string item);
	static void relational_optr(std::string optr, std::vector<std::string> actualLineWOWS, long wowsPos, long printedPos, long lineNum, 
								lineManager *relevantLines);
};

#endif

```
```

//ebnfFunctions.cpp
#include "ebnfFunctions.h"
//...
bool isSpecialChar(std::string varInQuestion){
	for(int i = 0; i < varInQuestion.length(); i++){
		if(not(utilityFunctions<std::string>::isInStr(varInQuestion.at(i), "=-+/*<>")))
			return false;
	}//for
	return true;
}//isSpecialChar

bool properNum(std::string var){
	for(int i = 0; i < var.length(); i++){
		if(not(utilityFunctions<std::string>::isInStr(var.at(i), "0123456789")))
			return false;
	}
	return true;
}//properVar()
//...

```
```

//utilityFunctions.h
#ifndef utilityFunctions_h
#define utilityFunctions_h

#include <vector>
#include <iostream>
#include <string>
#include <sstream>
//#include <sys/stat.h>
#include "ebnfFunctions.h"

template<class T>
class utilityFunctions{
public:
	static void printVect(std::vector<T> vect){
		std::cout << "\nBeg printVect" << std::endl;
		for(unsigned int itr = 0; itr < vect.size(); itr++){
			std::cout << vect.at(itr) << "\n";
		}
		std::cout << "End printVect" << std::endl;
	}//printVect()
	
	static std::string to_string(T t, std::ios_base & (*f)(std::ios_base&))
	{
		std::ostringstream oss;
		oss << f << t;
		return oss.str();
	}//to_string()
	
	static long findFirstInstance(std::vector<T> toFind, std::vector<T> findIn){
		long foundCtr = 0;
		for(long i = 0; i < findIn.size(); i++){
			if(toFind.at(0) == findIn.at(i)){
				foundCtr = 0;
				for(long pairItr = 0; pairItr < toFind.size() && pairItr+i < findIn.size() ; pairItr++){
					if(toFind.at(pairItr) == findIn.at(pairItr+i))
						foundCtr++;
					if(foundCtr == toFind.size())
						return i;
				}//for
			}//if
		}//for
		return -1;
	}//findFirstInstance()
	
	static bool isInStr(char c, std::string s);
	static bool strContains(std::string targetStr, std::string libOfVals);
	
};//class utilityFunctions

#endif

```
```

//utilityFunctions.cpp
#include "utilityFunctions.h"

bool isInStr(char c, std::string s){
	std::string::size_type pos = s.find(c);
	if(std::string::npos != pos)
		return true;
	else
		return false;
}//isInStr()
//...

```
If anyone can help me figure out this problem that would be great. As always, thanks in advance!

---

### Post by ju2wheels on 2010-04-13
In ebnFunctions.h you forgot to specify the class on the function definitions...

```

//ebnfFunctions.cpp
#include "ebnfFunctions.h"
//...
bool ebnFunctions::isSpecialChar(std::string varInQuestion){
	for(int i = 0; i < varInQuestion.length(); i++){
		if(not(utilityFunctions<std::string>::isInStr(varInQuestion.at(i), "=-+/*<>")))
			return false;
	}//for
	return true;
}//isSpecialChar

bool ebnFunctions::properNum(std::string var){
	for(int i = 0; i < var.length(); i++){
		if(not(utilityFunctions<std::string>::isInStr(var.at(i), "0123456789")))
			return false;
	}
	return true;
}//properVar()
//...

```

The same goes for your utility functions class, except for that one I think you also have to add the template to it, havent done templating in a while but I think it should be this:

```

//utilityFunctions.cpp
#include "utilityFunctions.h"

template <class T>
bool utilityFunctions<T>::isInStr(char c, std::string s){
	std::string::size_type pos = s.find(c);
	if(std::string::npos != pos)
		return true;
	else
		return false;
}//isInStr()
//...

```

Remember to add the template before each function definition.

---

### Post by StunnerAlpha on 2010-04-13
Oh wow thanks a lot man! That did the trick. For utilityFunctions I ended up just putting in the code in the .cpp file into the header as it still gave me the 'referenced from:' error. So to those interested, this is what I ended up doing for utilityFunctions.h in order for it to work properly(since it uses templates):
```

//utilityFunctions.h
//...
static bool isInStr(char c, std::string s){
		std::string::size_type pos = s.find(c);
		if(std::string::npos != pos)
			return true;
		else
			return false;
	}//isInStr()
	
	static bool strContains(std::string targetStr, std::string libOfVals){
		for(int i = 0; i < targetStr.length(); i++){
			std::string::size_type pos = libOfVals.find(targetStr.at(i));
			if(std::string::npos != pos)
				return true;
		}//for
		return false;
	}//strContains()

```
Thanks again!

---

