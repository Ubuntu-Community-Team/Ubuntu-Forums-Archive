---
title: "Linker Error: symbol(s) not found C++"
date: 2010-04-23
forum: Programming Talk
---

### Post by StunnerAlpha on 2010-04-23
Ey guys I have run into this strange error:
```
    cd /Users/.../scriptLang
    setenv MACOSX_DEPLOYMENT_TARGET 10.5
    /Developer/usr/bin/g++-4.0 -arch i386 -isysroot /Developer/SDKs/MacOSX10.5.sdk -L/.../scriptLang/build/Debug -F/.../scriptLang/build/Debug -filelist /.../scriptLang/build/scriptLanguage.build/Debug/scriptLanguage.build/Objects-normal/i386/scriptLanguage.LinkFileList -mmacosx-version-min=10.5 -o /.../scriptLang/build/Debug/scriptLanguage
Undefined symbols:
  "ebnfFunctions::Tokenize(std::basic_string<char, std::char_traits<char>, std::allocator<char> >, __gnu_debug_def::vector<std::basic_string<char, std::char_traits<char>, std::allocator<char> >, std::allocator<std::basic_string<char, std::char_traits<char>, std::allocator<char> > > >&, std::basic_string<char, std::char_traits<char>, std::allocator<char> >)", referenced from:
      _main in main.o
      _main in main.o
ld: symbol(s) not found
collect2: ld returned 1 exit status


```

Here is the relevant code:
```

#include "ebnfFunctions.h"

//...

void Tokenize(const std::string str, std::vector<std::string>& tokens, const std::string delimiters = " "){
	std::string::size_type begDelPos = str.find_first_of(delimiters, 0);
	std::string::size_type begCmdPos = str.find_first_not_of(delimiters, 0);
	std::string::size_type endCmdPos = str.find_first_of(delimiters, begCmdPos);
	
	while(std::string::npos != begDelPos|| std::string::npos != begCmdPos || std::string::npos != endCmdPos){
		try{
			while(begDelPos < begCmdPos){
				tokens.push_back(str.substr(begDelPos, 1));
				begDelPos = str.find_first_of(delimiters, begDelPos+1);
			}//while
			tokens.push_back(str.substr(begCmdPos, endCmdPos - begCmdPos));
			
			// Skip delimiters.  Note the "not_of"
			begCmdPos = str.find_first_not_of(delimiters, endCmdPos);
			// Find next "non-delimiter"
			endCmdPos= str.find_first_of(delimiters, begCmdPos);
		}//try
		catch(...){ //out of index error will occur upon the last iteration of loop
			//proceed elegantly
		}
	}//while
}//Tokenize

```
```

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
	static long charTypeAstrkBegCmnt(std::string line, std::vector<std::string> vectLine);
	static long charTypeAstrkEndCmnt(std::string line, std::vector<std::string> vectLine);
	static long charTypeFSCmnt(std::string line, std::vector<std::string> vectLine);
	static bool isSpecialChar(std::string varInQuestion);
	static bool properNum(std::string var);
	static bool properVar(std::string var);
	static bool appropVal(std::string item);
	static void relational_optr(std::string optr, std::vector<std::string> actualLineWOWS, long wowsPos, long printedPos, long lineNum, 
								lineManager *relevantLines);
	static void evaluate(std::string optr ,long wowsPos, std::vector<std::string> actualLineWOWS);
	static void Tokenize(const std::string str, std::vector<std::string>& tokens, const std::string delimiters = " ");
};

#endif

```
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
//#include "evaluate.h"


//TODO: 

using namespace std;

//...
int main(int argc, char **argv){	
	Stack = new stack<universalType>;
	
//...
		
	if(FileExists(fileName)){
		string line = "";
		string lineWOC = ""; //lineWithOutComments
		ifstream infile;
		infile.open(fileName.c_str());
		for(long i = 0; !infile.eof(); i++)
        {
			if(not closeBracePos.posUntouched()){ //reset positions if open/close brace pair found
				openBracePos.initialize();
				closeBracePos.initialize();
			}
			
	        getline(infile,line);
			
			cout << "line " << i+1 << ":\n";
			vector<string> tokenizedLine;
			ebnfFunctions::Tokenize(line, tokenizedLine, " <>*={}().,;'\"/-+\\");
			relevantLines->addLn(tokenizedLine);
			relevantLines->addLn(line);
			//lineVect.push_back(line);
			lineWOC = helperFunctions<string>::parseOutComments(line, ignoreLineCtr, i+1, relevantLines);
			
			ebnfFunctions::Tokenize(lineWOC, tokens, " <>*={}().,;'\"/-+\\");
			tokensWOWS = parseOutWhiteSpace(tokens);
			syntacticalTokensWOWS = helperFunctions<string>::parseOutQuotations(tokensWOWS);
			tokensVect.push_back(tokens);
//...

```
Any idea what's wrong? Thanks!

---

### Post by PaulM1985 on 2010-04-23
I can't see the declaration of the "tokens" variable in the second call to tokenize in main().

In the tokenise method, I think you are ok to do this:

const std::string delimiters = " ")

in the header but not in the implementation.

Paul

---

### Post by Zugzwang on 2010-04-23
> **StunnerAlpha said:**
> 
Any idea what's wrong? Thanks!

I think that this is an easy one: See that you have "void Tokenize(const std::string str, std::vector<std::string>& tokens, const std::string delimiters = ...)" defined in "the relevant code". I think that this should rather be "void ebnfFunctions::Tokenize(...)".

---

### Post by StunnerAlpha on 2010-04-24
Thanks guys, I had to add the ebnfFunctions:: before the function name in the implementation file. I saw my error on my own this morning... that's what I get for working till 4AM... Thanks again!

---

