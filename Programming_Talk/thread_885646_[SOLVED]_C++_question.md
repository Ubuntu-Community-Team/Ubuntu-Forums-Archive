---
title: "[SOLVED] C++ question"
date: 2008-08-10
forum: Programming Talk
---

### Post by Kolmogorov on 2008-08-10
Hi everyone, 

I have a bug in my program but i can't find where...

```
// prob6.cpp
// Write a program that asks the user to enter an hour value and a minute value.
// The main() function should then pass these two values to a type void function
// that displays the two values in the format shown in the following sample run:
// 	Enter the number of hours: 9
//	Enter the number of minutes: 28
//	Time: 9:28
// by Steeve Brechmann.

#include<iostream>

void hrmin(int hr, int min);	// function prototype

int main(void)
{
	using namespace std;

	int hr, min;		// hr = hour, min = minutes
	
	// Print an introduction.
	cout << endl << "This program display the time in the format hh:mm." << endl;
	cout << "Enter the number of hours: ";
	// Get user input.
	cin  >> hr;
	cout << "Enter the number of minutes: ";
	cin  >> min;
	// Display results.
	cout << "Time: " << hrmin(hr,min) << endl << endl;

	return(0);
}

void hrmin(int hr, int min)
{
	using namespace std;

	cout << hr << ":" << min;
}
```

When i try to compile it, i have the following errors:

```
steeve@steeve-laptop:~/Documents/cpp/ch02$ g++ prob6.cpp -o prob6
prob6.cpp: In function ‘int main()’:
prob6.cpp:28: error: no match for ‘operator<<’ in ‘std::operator<< [with _Traits = std::char_traits<char>](((std::basic_ostream<char, std::char_traits<char> >&)(& std::cout)), ((const char*)"Time: ")) << hrmin(hr, min)’
/usr/include/c++/4.2/ostream:112: note: candidates are: std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ostream<_CharT, _Traits>& (*)(std::basic_ostream<_CharT, _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:121: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_ios<_CharT, _Traits>& (*)(std::basic_ios<_CharT, _Traits>&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:131: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::ios_base& (*)(std::ios_base&)) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:169: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:173: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:177: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(bool) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/bits/ostream.tcc:92: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:184: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(short unsigned int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/bits/ostream.tcc:106: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:195: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(unsigned int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:204: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long long int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:208: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long long unsigned int) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:213: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(double) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:217: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(float) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:225: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(long double) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/ostream:229: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(const void*) [with _CharT = char, _Traits = std::char_traits<char>]
/usr/include/c++/4.2/bits/ostream.tcc:120: note:                 std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::operator<<(std::basic_streambuf<_CharT, _Traits>*) [with _CharT = char, _Traits = std::char_traits<char>]
```

Can anyone one figure out what i'm doing wrong ?

Thanks !

---

### Post by paukku92 on 2008-08-10
The bug is in the following row:

```
cout << "Time: " << hrmin(hr,min) << endl << endl;
```

The function hrmin doesnt return anything to print.

The solution would be:

```
cout << "Time: ";
hrmin(hr,min);
cout << endl << endl;
```

---

### Post by Kolmogorov on 2008-08-10
You are so damn right, i forget about that ! Thanks !!!

---

