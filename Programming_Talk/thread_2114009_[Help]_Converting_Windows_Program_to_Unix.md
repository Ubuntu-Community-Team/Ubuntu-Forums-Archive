---
title: "[Help] Converting Windows Program to Unix"
date: 2013-02-08
forum: Programming Talk
---

### Post by Moose1004 on 2013-02-08
Error: 
main.cpp: In function \u2018void passOne(std::string, SymbolsTable&)\u2019:
main.cpp:24: error: no matching function for call to \u2018std::basic_ifstream<char, std::char_traits<char> >::open(std::string&)\u2019
/usr/include/c++/4.4/fstream:525: note: candidates are: void std::basic_ifstream<_CharT, _Traits>::open(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]

when using: g++ -c main.cpp and g++ -Wall -pedantic -ansi main.cpp


```

#include<iostream>
#include<string>
#include<vector>
#include<sstream>
#include<fstream>

#include "symbols_table.h"
#include "operations.h"

void passOne(string fileName, SymbolsTable& st)
{
	Operations o;
	ifstream inFile;
	inFile.open(fileName);
	string tempString;
	string tempLabel;
	string tempOp;
	int address = 0;

	while(getline(inFile, tempString))
	{
		//cout << tempString << endl;
		istringstream iss (tempString);
		
		iss >> tempLabel;

		//cout << tempLabel << endl;
		if(tempLabel.compare("#") == 0)
		{
			//cout << "#" << endl;
		}

		//if it's not an operation, it's not already a declared label, it's not a comment
		//may need to throw exception output for duplicated labels?
		if(!o.isOperation(tempLabel) && !st.isLabel(tempLabel) && tempLabel.compare("#") != 0)// && tempString.compare("") != 0)
		{

			//cout << address << " Label" << endl;
			st.addLabel(tempLabel, address); //the VM's address
			iss >> ws >> tempOp;

			if(o.isOperation(tempOp))
			{
				address += 3;	//increase the address by 3 for an instruction
			}
			else
			{
				address++;	//increase the address by 1 byte for a directive
			}
		}
		else if(o.isOperation(tempLabel) && tempLabel.compare("#") != 0)
		{
			//cout << address << " Operation" << endl;
			address += 3;	//increase the address by 3 for an instruction
		}
				
		//inFile.ignore ( std::numeric_limits<std::streamsize>::max(), '\n' );
		//cout <<"address: " << address << endl << endl;
	}
}

int main(int argc, char* argv[]){ 
	SymbolsTable st;
	//bool test;
	string s = argv[1];

	passOne(argv[1], st);
	st.printLabels();
}

```

---

### Post by Moose1004 on 2013-02-08
Not sure how to change the status of this post, but my issue has been resolved.

Original: ```
void passOne(string fileName, SymbolsTable& st)
```

New: ```
void passOne(char* fileName, SymbolsTable& st)
```

---

