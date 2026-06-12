---
title: "G++ help"
date: 2009-05-22
forum: Programming Talk
---

### Post by piasdom on 2009-05-22
hello all,
how do i get this to continue to add until the user hit enter twice?
i would like to be able to add more then just two numbers. thanks for any help and i hope i'm in the correct forum. Thanks !
---------------------------------------------------------
	case 5:
		cout << "addition\n";
		cout << "enter first #: ";
		cin >> user_input;
		cout << "enter second #: ";
		cin >> user_input2;
		cout << user_input << " + " << user_input2 << " = "<< user_input+user_input2 << endl;
----------------------------------------------------------

i'm using G++ in ubuntu hardy.
i'm learning this for work. they don't have time to teach me, but i have
plenty of time:) and help would be greatly appreciated.

---

### Post by SadaraX on 2009-05-23
Sounds simply enough. You probably want to use a loop. I do not know what you want to do with all the numbers you collect, whether you want to display them or add them all together. But this should get you started.

```

case 5:
#include <cstdlib> // I'm assuming you are using modern C++

std::string str = "";
std:vector<int> numbers(); // to hold the number input
cout << "Type 'stop' to finish" << endl;
cout << "addition" << endl;
while( str != "stop" ) // collect the number input
{
  cout << "enter #: ";
  cin >> str; // get input
  if( str != "stop" ) // check if we should stop
  {
    numbers.push_back( atoi( str.c_str() ) ); // convert to an integer and store the input for later
  }
}
cout << "The input numbers: ";
for( int i = 0; i < numbers.length(); i++) // process all the stored input
{
  cout << numbers[i] << endl;
  // Optionally you could add them all here....
}
cout << endl;

```

---

### Post by piasdom on 2009-05-23
> **SadaraX said:**
> Sounds simply enough. You probably want to use a loop. I do not know what you want to do with all the numbers you collect, whether you want to display them or add them all together. But this should get you started.

```

case 5:
#include <cstdlib> // I'm assuming you are using modern C++

std::string str = "";
std:vector<int> numbers(); // to hold the number input
cout << "Type 'stop' to finish" << endl;
cout << "addition" << endl;
while( str != "stop" ) // collect the number input
{
  cout << "enter #: ";
  cin >> str; // get input
  if( str != "stop" ) // check if we should stop
  {
    numbers.push_back( atoi( str.c_str() ) ); // convert to an integer and store the input for later
  }
}
cout << "The input numbers: ";
for( int i = 0; i < numbers.length(); i++) // process all the stored input
{
  cout << numbers[i] << endl;
  // Optionally you could add them all here....
}
cout << endl;

```
sorry if i wasn't clear(new to G++) i'm trying to get the user to add number.2 to 10000 numbers. i want to add the number together and give the sum to the user. so he could add two numbers or 10000(unlimited amount of numbers). then end it somehow..i thought of hitting enter twice. but i don't ever know if this is possible and thanks for the quick response SadaraX.

p.s. i don't know how to see what version of G++ i'm using.but just started learning this about 6 months.

---

### Post by SadaraX on 2009-05-23
Just FYI: G++ is the compiler, while C++ is the language. Good luck on learning more.

```

case 5:
#include <cstdlib> // I'm assuming you are using modern C++

std::string str = "";
std:vector<int> numbers(); // to hold the number input
cout << "Type 'stop' to finish" << endl;
cout << "addition" << endl;
while( str != "stop" ) // collect the number input
{
  cout << "enter #: ";
  cin >> str; // get input
  if( str != "stop" ) // check if we should stop
  {
    numbers.push_back( atoi( str.c_str() ) ); // convert to an integer and store the input for later
  }
}
cout << "Answer: ";
long int answer = 0;
for( int i = 0; i < numbers.length(); i++) // process all the stored input
{
  answer = answer + numbers[i];
}
cout << answer << endl;

```

This code will accept user input pretty much indefinitely. They can enter 10,000 numbers (actually a lot more), then type stop, and the program will add them all together.

Isn't this what you want?

---

### Post by piasdom on 2009-05-23
> **SadaraX said:**
> Sounds simply enough. You probably want to use a loop. I do not know what you want to do with all the numbers you collect, whether you want to display them or add them all together. But this should get you started.

```

case 5:
#include <cstdlib> // I'm assuming you are using modern C++

std::string str = "";
std:vector<int> numbers(); // to hold the number input
cout << "Type 'stop' to finish" << endl;
cout << "addition" << endl;
while( str != "stop" ) // collect the number input
{
  cout << "enter #: ";
  cin >> str; // get input
  if( str != "stop" ) // check if we should stop
  {
    numbers.push_back( atoi( str.c_str() ) ); // convert to an integer and store the input for later
  }
}
cout << "The input numbers: ";
for( int i = 0; i < numbers.length(); i++) // process all the stored input
{
  cout << numbers[i] << endl;
  // Optionally you could add them all here....
}
cout << endl;

```
thanks,this is what i'm looking for.got some new things in there but it gets me headed in the right direction. off to work on it. thanks SadaraX

---

