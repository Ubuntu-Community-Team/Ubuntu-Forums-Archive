---
title: "[C++] Can't compile a simple file I/O application - need help !"
date: 2009-05-29
forum: Programming Talk
---

### Post by ActiveFrost on 2009-05-29
How to fix this /error/ ( look at the details below ) ?

**Sample.cpp**
```
#include <iostream>
#include <fstream>
#include <string>
#include <stdlib.h>

using namespace std;

int main() {
	
	string homedir = getenv("HOME");
	string file_path = homedir + "/" + "MYFILE.txt";
	
	ofstream myFile;
	myFile.open(file_path);
	myFile << "One line of text ! \n";
	myFile.close();

	return 0;
	
}
```

**Compilation error :**
```
dainis@suncore:~/Desktop/temp$ g++ Sample.cpp -o Sample
Sample.cpp: In function ‘int main()’:
Sample.cpp:14: error: no matching function for call to ‘std::basic_ofstream<char, std::char_traits<char> >::open(std::string&)’
/usr/include/c++/4.3/fstream:626: note: candidates are: void std::basic_ofstream<_CharT, _Traits>::open(const char*, std::_Ios_Openmode) [with _CharT = char, _Traits = std::char_traits<char>]
```

---

### Post by Dolf123 on 2009-05-29
"myFile.open(file_path);"

Doesn't exist. Check the function name and the arguments you are passing, make sure it all matches.

Edit: I tried it for you, this should work "myFile.open( file_path.c_str() );". You need to pass a character array instead of the string class instance.

---

### Post by Habbit on 2009-05-29
Simple, as the error message clearly says (which is an odd thing when templates are involved), you are trying to call a function with an argument set it does not support. In particular, no overload of ofstream::open takes a string - it takes a char*. In order to get a C-string from a C++ std::string, invoke its c_str() method.

---

### Post by ActiveFrost on 2009-05-29
> **Dolf123 said:**
> "myFile.open(file_path);"

Doesn't exist. Check the function name and the arguments you are passing, make sure it all matches.

Edit: I tried it for you, this should work "myFile.open( file_path.c_str() );". You need to pass a character array instead of the string class instance.

Thanks a lot - works like a charm :)

---

