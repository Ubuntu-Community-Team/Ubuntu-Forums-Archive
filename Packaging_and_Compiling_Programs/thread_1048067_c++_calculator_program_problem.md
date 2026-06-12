---
title: "c++ calculator program problem"
date: 2009-01-23
forum: Packaging and Compiling Programs
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

### Post by meatpan on 2009-01-23
There are quite a few errors in your code.  

-Check to make sure all of your strings are fully quoted.  
-case statements should end in ':', not ';'
-re-evaluate our 'cin' operations.  You are reading variables 'in' to the std::endl char.  Let me know if this doesn't make sense.
Your cin shoudl be like:
cin>>dnumber1;
cin>>cChar;
cin>>dnumber2;

---

### Post by octopusfinley on 2009-01-23
Thank you very much. I was miraculously able to fix a lot of this earlier this morning, and your information is most appreciated.

---

