---
title: "c++ attempted program fails"
date: 2009-01-23
forum: Programming Talk
---

### Post by octopusfinley on 2009-01-23
Alright everyone. I'm just learning C++ and for my newest self project, I'm trying to make a calculator. Now, my error messages for this are truly awe inspiring and I just can't understand a word of the output (plus it's like ten pages, so I can't put it here). Can anyone give me some hints as to where I'm going wrong? (note, this is completely on my own, with no formal training and so I am most definitely using about 80-90 percent of these functions wrong).

#include <iostream>
using namespace std;

int main ()
{
char cChar;
double dnumber1;
double dnumber2;
char cDoagain;

do
{
system ("CLS");
cout<<"Please enter the first digit you'd like to use"<<endl;
cin>>dnumber1>>endl;
cout<< "Please select the operation"<<"+, -, * or /"<<endl;
cin>>cChar>>endl;
cout<<"Please enter second number"<<endl;
cin>>dnumber2>>endl;

switch (cChar)
{
case '+';
cout<<dnumber1<<'+'<<dnumber2<<'='<<(dnumber1 + dnumber2)<<endl;
break;
case '-';
cout<<dnumber<<'-'<<dnumber2<<'='<<(dnumber1 - dnumber2)<<endl;
break;
case '*';
cout<<dnumber1<<'*'<<dnumber2<<'='<<(dnumber1 * dnumber2)<<endl;
break;
case 'x';
cout<<dnumber1<<'x'<<dnumber2<<'='<<(dnumber1 *dnumber2)<<endl;
break;
case 'X';
cout<<dnumber1<<'X'<<dnumber2<<'='<<(dnumber1 * dnumber2)<<endl;
break;
case '/';
if (dnumber2 == 0) {
cout<<"Can't divide something by zero"<<
}else {
cout<<dnumber1<<'/'<<dnumber2<<'='<<(dnumber1 / dnumber2)<<endl;
}break;
default:
cout<<"That's not a valid operation<<endl;
}
cout<<"Would you like to make another operation?"<<"Y/n?"<<endl;
cin>>cDoagain;
}while(cDoagain == 'Y' || cDoagain == 'y');
return 0;
}

so if you've got a couple moments to waste here in the wee hours of the morning, your help is much appreciated.
finley

---

### Post by Zorgoth on 2009-01-23
"if (dnumber2 == 0) {
cout<<"Can't divide something by zero"<<
}else {"

No semicolon.  In the future, please indent your code and incidentally you don't need curly brackets after an "if" if it's just one line and that usually makes it easier to read.  A single semicolon or bracket error will usually cause an amazing number of errors.  I'm going to go test your code now.

---

### Post by Zorgoth on 2009-01-23
I got it working:

: not ; after cases in a switch and you're missing a quote after your "else" cout also.  cin >> endl; doesn't work and causes most of the errors.  dnumber is not declared.  I think that was all the errors.

---

### Post by Zorgoth on 2009-01-23
Oh and system("clear") would be the appropriate command rather than "cls".

Here is a working version:

```

#include <iostream>
using namespace std;

int main ()
{
char cChar;
double dnumber1;
double dnumber2;
char cDoagain;

do
	{
	system ("clear");
	cout<<"Please enter the first digit you'd like to use"<<endl;
	cin>>dnumber1;
	cout<< "Please select the operation"<<"+, -, * or /"<<endl;
	cin>>cChar;
	cout<<"Please enter second number"<<endl;
	cin>>dnumber2;
	switch (cChar)
		{
		case '+' :
		cout<<dnumber1<<'+'<<dnumber2<<'='<<(dnumber1 + dnumber2)<<endl;
		break;
		case '-' :
		cout<<dnumber1<<'-'<<dnumber2<<'='<<(dnumber1 - dnumber2)<<endl;
		break;
		case '*' :
		cout<<dnumber1<<'*'<<dnumber2<<'='<<(dnumber1 * dnumber2)<<endl;
		break;
		case 'x' :
		cout<<dnumber1<<'x'<<dnumber2<<'='<<(dnumber1 *dnumber2)<<endl;
		break;
		case 'X' :
		cout<<dnumber1<<'X'<<dnumber2<<'='<<(dnumber1 * dnumber2)<<endl;
		break;
		case '/' :
		if (dnumber2 == 0) cout<<"Can't divide something by zero";
		else cout<<dnumber1<<'/'<<dnumber2<<'='<<(dnumber1 / dnumber2)<<endl;
		break;
		default:
		cout<<"That's not a valid operation<<endl";
		}
        cout<<"Would you like to make another operation?"<<"Y/n?"<<endl;
        cin>>cDoagain;
        } while(cDoagain == 'Y' || cDoagain == 'y');
return 0;
}

```

Hope this helps, and that reminds me, use code tags in the future.

---

