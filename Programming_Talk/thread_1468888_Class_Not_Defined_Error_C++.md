---
title: "Class Not Defined Error C++"
date: 2010-05-01
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-05-01
Ey guys, I am having a hard time figuring out this error(googling wasn't much help). I am receiving a class not declared error:
```

/Users/...helperFunctions.h:99: error: 'builtins' has not been declared

```
Here is the relevant code:
```

//helperFunctions.h
#ifndef helperFunctions_h
#define helperFunctions_h

#include <vector>
#include <string>
#include "globals.h"
#include "builtins.h"
#include "utilityFunctions.h"

//class builtins;

template<class T>
class helperFunctions{
public:
//...
	static void builtinSearchAndPrep(std::vector<std::string> actualLine, int actualLineIndex, std::vector<std::string> actualLineWOWS){
		int wowsPos;
		if(actualLine.at(actualLineIndex) == "print"){
			std::vector<std::string> evalLine(actualLine);
			evalLine.erase(evalLine.begin());
			builtins::print(evalLine); //PROBLEM AT THIS LINE
		}
	}//builtinSearchAndPrep()
//...
};//class helperFunctions

#endif

```
```

//builtins.h
#ifndef builtins_h
#define builtins_h

#include <vector>
#include <string>
#include "globals.h"
#include "utilityFunctions.h"
#include "evaluate.h"

class builtins{
public:
	static void print(std::vector<std::string> evalLine);
};

#endif

```
```

//main.cpp
#include <iostream>
#include <fstream>
#include <string>
#include <algorithm>
#include <vector>
#include <stdexcept>
#include <sys/stat.h>
#include <sstream>
#include "filePos.h"
#include "lineManager.h"
#include "utilityFunctions.h"
#include "helperFunctions.h"
#include "ebnfFunctions.h"
#include "stack.h"
#include "globals.h"
#include "builtins.h"
#include "evaluate.h"


using namespace std;

//...
int main(int argc, char **argv){
//...
}//main

```
```

//utilityFunctions.h
#ifndef utilityFunctions_h
#define utilityFunctions_h

#include <vector>
#include <iostream>
#include <string>
#include <sstream>
#include "ebnfFunctions.h"

template<class T>
class utilityFunctions{
public:
//...
};//class utilityFunctions

#endif

```
If there is cyclic referencing, it is not obvious, and I have tried forward declarations, but those don't work but instead make more errors. Thanks for any help!

---

### Post by dwhitney67 on 2010-05-01
There's nothing wrong with the code you provided... other than you provided too little.

Once I commented out the inclusion of all of the header files that you neglected to post, everything compiled/linked fine.

A little bit of advice....

1.  DO NOT include header files that are not necessary to make the "unit" (whether this be a header or implementation file) compilable.

2.  ALWAYS include your project header files BEFORE including system header files.



P.S.  In reference to #1 (and FWIW, #2) above.... please, is this really necessary for main.cpp???????
```

#include <iostream>
#include <fstream>
#include <string>
#include <algorithm>
#include <vector>
#include <stdexcept>
#include <sys/stat.h>
#include <sstream>
#include "filePos.h"
#include "lineManager.h"
#include "utilityFunctions.h"
#include "helperFunctions.h"
#include "ebnfFunctions.h"
#include "stack.h"
#include "globals.h"
#include "builtins.h"
#include "evaluate.h"

```

---

### Post by StunnerAlpha on 2010-05-02
Ey thanks for the tips. I had actually been doing the opposite of what you are suggested(particularly with main.cpp). So I removed a couple of header files that I know aren't needed(removed evaluate.h and builtins.h). But yes, a lot of those are in fact necessary.
Here are the rest of the header files:
```

//filePos.h
#ifndef filePos_h
#define filePos_h

class filePos{
private:
	long row;
	long index;
public:
//...
}; //class filePos

#endif

```
```

//stack.h
#ifndef stack_h
#define stack_h

#include <iostream>
#include <list>
#include <string>
#include "stackNode.h"

using namespace std;

template <class T>
class stack{
private:
	list< stackNode<T> > stackList;
public:
	stack();
	void addVar(string var, T val);
	T getVal(string var);
}; //class stack

template <class T>
stack<T>::stack(){
	
}
//...
#endif

```
```

//stackNode.h
#ifndef stackNode_h
#define stackNode_h

#include <string>

using namespace std;

struct universalType{
	//enum type{null, nonNull};
	bool valid; //indicates if struct instance is a valid one
	union{
		int ifInt;
		char ifChar;
	};//union
};

template <class T>
class stackNode{
//...
}

template <class T>
stackNode<T>::stackNode(string var, T val){
	variable = var;
	value = val;
}//stackNode constructor
//...
#endif

```
```

//lineManager.h
#ifndef lineManager_h
#define lineManager_h

#include <string>
#include <vector>
#include "utilityFunctions.h"

class lineManager{
private:
//...
};//class lineManager
//...

#endif

```
```

//ebnfFunctions.h
#ifndef ebnfFunctions_h
#define ebnfFunctions_h

#include <vector>
#include <string>
#include "lineManager.h"
#include "utilityFunctions.h"
#include "globals.h"

class lineManager;

class ebnfFunctions{
public:
//...
};

#endif

```
```

//globals.h
#ifndef globals_h
#define globals_h

#include "stack.h"

extern stack<universalType> *Stack;

#endif

```
```

#ifndef evaluate_h
#define evaluate_h

#include <string>
#include <vector>
#include <iostream>
#include "utilityFunctions.h"
#include "helperFunctions.h"

class evaluate{
public:
//...
};//class evaluate

#endif

```
And by this sentence: "ALWAYS include your project header files BEFORE including system header files." do you mean that I should for example change this:
```

#include <string>
#include <vector>
#include <iostream>
#include "utilityFunctions.h"
#include "helperFunctions.h"

```
to this?
```

#include "utilityFunctions.h"
#include "helperFunctions.h"
#include <string>
#include <vector>
#include <iostream>

```
Thanks!

---

### Post by StunnerAlpha on 2010-05-02
I discovered what I added that caused the problem. Here is the relevant code:
```

//evaluate.h
#ifndef evaluate_h
#define evaluate_h

#include <string>
#include <vector>
#include <iostream>
#include "utilityFunctions.h"
//#include "helperFunctions.h" //the problem occurs when I add this line

class evaluate{
public:
	static std::string cleanStr(std::string& rawStr);
	static std::string evalToRaw(std::vector<std::string> evalLine);
	static std::string evalAdditionOpr(std::string leftOperand, std::string rightOperand);
};//class evaluate

#endif

```
When I add the above indicated line, it gives me the error that builtin has not been declared. But how do I work around this, and why is this occurring? Thanks!

---

### Post by dwhitney67 on 2010-05-02
> **StunnerAlpha said:**
> ...

And by this sentence: "ALWAYS include your project header files BEFORE including system header files." do you mean that I should for example change this:
```

#include "utilityFunctions.h"
#include "helperFunctions.h"
#include <string>
#include <vector>
#include <iostream>

```
Thanks!

Yes, that is correct... but bear in mind, this is merely my opinion.  I've been developing s/w for 20+ years, so hopefully my opinion is worth something.

The premise for this methodology is so that it helps identify very quickly which header files can stand on their own when being compiled, versus masking an issue with a header file that is inadvertently dependent upon another for a critical include file.

For instance, in your original posting, you have main.cpp including <vector>.  Suppose that include is missing from one of your header files that actually requires it --- well, you would never know based on the ordering of your header files.

Btw, I still cannot believe that your main.cpp requires include statements for <vector>, <string>, etc.  The work should be done within your class objects, not the main() function.

---

### Post by dwhitney67 on 2010-05-02
> **StunnerAlpha said:**
> I discovered what I added that caused the problem. Here is the relevant code:
```

//evaluate.h
#ifndef evaluate_h
#define evaluate_h

#include <string>
#include <vector>
#include <iostream>
#include "utilityFunctions.h"
//#include "helperFunctions.h" //the problem occurs when I add this line

class evaluate{
public:
	static std::string cleanStr(std::string& rawStr);
	static std::string evalToRaw(std::vector<std::string> evalLine);
	static std::string evalAdditionOpr(std::string leftOperand, std::string rightOperand);
};//class evaluate

#endif

```
When I add the above indicated line, it gives me the error that builtin has not been declared. But how do I work around this, and why is this occurring? Thanks!

I have no idea what is causing this; as I stated earlier, I was able to compile all of your code from your original post.

And unless I see a compelling reason for you to include <helperfunctions> in the header file shown above, I would recommend that you remove it from the include list.

P.S.  When passing complex objects to methods, avoid passing by value, for this makes a deep copy of the object, which in turn is CPU/Memory expensive.  Pass these objects by reference.

---

### Post by StunnerAlpha on 2010-05-05
Thanks for all the tips dwhitney67, I'll be sure to take that advice. I ended up forward declaring the helperFunctions class and it doesn't complain anymore:
```

//evaluate.h
#ifndef EVALUATE_H
#define EVALUATE_H

#include <string>
#include <vector>
#include <iostream>
#include "utilityFunctions.h"
//#include "helperFunctions.h" //problematic line

template <class T>
class helperFunctions;

class evaluate{
public:
//...

```
However I am getting another strange error that's not obvious to me:
```
error: incomplete type 'helperFunctions<std::string>' used in nested name specifier
```
and it's at the indicated line:
```

//evaluate.cpp
#include "evaluate.h"

//...

std::string evaluate::evalToRaw(std::vector<std::string> evalLine){
	std::vector<std::string> evalLineWOWS;
	evalLineWOWS = helperFunctions<std::string>::parseOutWhiteSpace(evalLine); //ERROR HERE
	utilityFunctions<std::string>::printVect(evalLine);
	std::string rawLine = "";
	bool withinQuotations = false;
	bool encounteredAdd = false;
	bool encounteredQuotes = false;
	for(int i = 0; i < evalLine.size(); i++){
		if(evalLine.at(i) == "+"){
			encounteredAdd = true;
			rawLine = evalAdditionOpr(utilityFunctions<std::string>::grabBetween("+", evalLine, 0, false), \
							utilityFunctions<std::string>::grabBetween("+", evalLine,i+1));
			cout << "rawLine: " << rawLine << endl;
		}
		if(evalLine.at(i) == "\"")
			encounteredQuotes = true;
	}//for
	if(!encounteredAdd){
		if(encounteredQuotes){
			std::vector<std::string> dblQuote;
			dblQuote.push_back("\"");
			long pos = utilityFunctions<std::string>::findFirstInstance(dblQuote, evalLine);
			rawLine.append(utilityFunctions<std::string>::grabBetween("\"", evalLine, pos));
			rawLine = cleanStr(rawLine);
			withinQuotations = true;
			std::cout << "rawLine2: " << rawLine << std::endl;
		}//if '"'
		else{
			for(int i = 0; i < evalLine.size(); i++){
				if(evalLine.at(i) != " " || evalLine.at(i) != "\t"){
					universalType uT;
					uT = Stack->getVal(evalLine.at(i));
					if(uT.valid)
						rawLine.append(utilityFunctions<int>::to_string(uT.ifInt,std::dec));
				}
			}
		}//else
	}//if
	return rawLine;
}//evalToRaw()

//...

```
And here is the relevant code in helperFunctions.h:
```

//helperFunctions.h
#ifndef helperFunctions_h
#define helperFunctions_h

#include <vector>
#include <string>
#include "globals.h"
#include "builtins.h"
#include "utilityFunctions.h"

template<class T>
class helperFunctions{
public:
//..
	static std::vector<std::string> parseOutWhiteSpace(std::vector<std::string> tokens){
		std::vector<std::string> tokensWOWS;
		for(long i = 0; i < tokens.size(); i++){
			if(not(tokens.at(i) == " "))
				tokensWOWS.push_back(tokens.at(i));
		}//for
		return tokensWOWS;
	}//parseOutWhiteSpace
//...
};//class helperFunctions

```
Any help greatly appreciated, thanks!

---

### Post by dwhitney67 on 2010-05-05
I haven't a clue what you are trying to accomplish, but it would seem that what's really biting you is your ill-conceived (over)use of templated functions/classes.

Basically, I don't quite understand why your helper functions are within a template class.  For instance, parseOutWhiteSpace() -- it doesn't even use the typename T that is defined for the class in which it resides.  I know for sure that you cannot parse out white-space from an int or a double, much less from a class called Foo.  Since it will only work on strings, would it not be better to place the method in a standalone library, perhaps even within a namespace?

Anyhow, without your complete code in which to experiment/compile on my own system, there isn't much else I can offer.  Maybe you should focus on tidying up the code, and avoid templates unless absolutely necessary.

---

### Post by StunnerAlpha on 2010-05-06
Hi dwhitney67, thanks for all the helpful responses. Good points there, I will be sure to make those changes. I have been considering just using namespaces for awhile but think I will finally make the change. Just a quick question though, in order to have good style would you declare namespaces with header and implementation files like you do with classes? If so could you give a quick example? Thanks!

---

### Post by dwhitney67 on 2010-05-06
Yes.

Header.h:
```

#ifndef HELPER_H
#define HELPER_H

#include <vector>
#include <string>

typedef std::vector<std::string> VecStrings;


namespace Helper
{
   VecStrings parseOutWhiteSpace(const VecStrings& tokens);

   //...
}

#endif

```

Helper.cpp:
```

#include "Helper.h"

namespace Helper
{
   VecStrings parseOutWhiteSpace(const VecStrings& tokens)
   {
      VecStrings tokensWOWS;

      for (VecStrings::const_iterator it = tokens.begin(); it != tokens.end(); ++it)
      {
         if (*it != " ")
         {
            tokensWOWS.push_back(*it);
         }
      }

      return tokensWOWS;
   }


   //...
}

```

---

### Post by StunnerAlpha on 2010-05-08
Thanks for all the help. I ended up just moving everything from builtins and evaluate into helperFunctions and I changed all classes that could be changed to namespaces. Marking as solved.

---

