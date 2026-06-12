---
title: "Generic Caesarian Cipher (rotN)"
date: 2007-01-22
forum: Programming Talk
---

### Post by Randomskk on 2007-01-22
I've just finished a quick and dirty rotN program in C++:

[www.randomskk.net/uploads/rotN.html](www.randomskk.net/uploads/rotN.html)

It's not exactly.. elegant, though. What do you guys think?

Also, as an aside: any ideas on how to get the current date (ie, 04, 28, etc) of the day of the month from C++?

---

### Post by xtacocorex on 2007-01-22
Not a bad program, one thing I would do is have it read the value of N from the command line. 

Here is some code I found (with comment saying where I got it) that does a string to integer conversion:
```

#include <string>
// STRING CONVERSION FROM CODEGURU
// http://www.codeguru.com/forum/showthread.php?t=231054
template <class T>
bool from_string(T& t,const std::string& s,std::ios_base& (*f)(std::ios_base&))
{
    std::istringstream iss(s);
    return !(iss >> f >> t).fail();
}

// Converts a string to an integer
int convStrInt(std::string inStr)
{
    // Variable Declaration
    int iVal;

    // The third parameter of from_string() should be 
    // one of std::hex, std::dec or std::oct
    if(from_string<int>(iVal, inStr, std::dec))
    {
        return iVal;
    }
    else
    {
        std::cout << "from_string failed" << std::endl;
        std::exit(1);
    }
} // End convStrInt

```I don't fully know how the first function works, but it does and does it very well.

---

### Post by Wybiral on 2007-01-22
If you want dynamic-esque objects in C++ string streams are the way to go...

```

#include <string>
#include <sstream>
#include <iostream>

using namespace std;

class dynamic {
	public:
		stringstream strValue;
		dynamic(){}

		template <typename T>
		void operator=(T value){strValue.str(""); strValue << value;}

		template <typename T>
		void operator<<(T value){strValue << value;}

		template <typename T>
		void operator>>(T& value){strValue >> value;}

		string c_str(){return strValue.str();}
		int    c_int(){return atoi(strValue.str().c_str());}
		float  c_flt(){return atof(strValue.str().c_str());}
};

int main(){
	dynamic myVariable;

	myVariable = 10.7;
	cout << myVariable.c_int()+ 3  << endl;
	cout << myVariable.c_flt()+ 3  << endl;
	cout << myVariable.c_str()+'3' << endl;

	myVariable = "";
	myVariable << "1";
	myVariable << 2;
	myVariable << 3.5;
	myVariable << 6;
	myVariable << "7";
	cout << myVariable.c_str() << endl;

	myVariable = myVariable.c_flt() * 2;
	cout << myVariable.c_str() << endl;

}

```

---

