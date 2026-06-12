---
title: "Seperating a Character in C++"
date: 2006-08-17
forum: Programming Talk
---

### Post by cobbweb on 2006-08-17
Hi, 
  I have a userInput kind of like this

cin >> userInput;

   I know the user input will be a character of to ie "G5" But I don't know how I can seperate the character. For instance I want; 

 char one = 'G';
 char two = '5';

Is there a member function that can complete this task??? Thanks any help is much apritiated, 

 Cobbweb

---

### Post by badactress on 2006-08-17
Hi CobbWebb! 

If userInput is a character array (or string) and you know the input will always be 2 characters then it's so simple..

try

cin >> userInput;

char one = userInput[0];
char two = userInput[1];

Hope this helps!
Norm

---

### Post by ifokkema on 2006-08-17
How about cin.get(), which will read one char from the input.

---

### Post by LordHunter317 on 2006-08-17
If it's really just two characters, then cin.get() would suffice and be smarter.

But it's almost never two characters.  It's almost always superior to read whole lines into a string, then split the string in various ways.

---

### Post by BreddS on 2006-08-18
"i created a program that prompts the user to give a psswrd, then the program stores the password. the program then checks the password. but when it gets to the part where it checks the password, no matter what i do, it never sees that the two strings are the same...i was wondering if i someone could point me in the right direction?

anyways, here is the code:

Code:
//store/check password
#include <iostream>
#include <cstdlib>
using namespace std;

class pswrd {
public:
      char ps[80], usr[80];
      int len;
      void set_ps (char *p) {strcpy(ps, p);}
      void check_ps () {
            printf(""\nPassword: "");
            cin>>usr;
            if(usr!=ps) cout<<endl<<""Access Denied"";
            else if(usr==ps) cout<<endl<<""Access Granted"";
       }
};

int main ()
{
    pswrd ob1;
    char p[80];
    printf(""Set Password: "");
    cin>>p;
    ob1.set_ps(p);
    ob1.check_ps();
    system(""PAUSE"");
}"

---

### Post by LordHunter317 on 2006-08-18
Don't ***ever, ever, ever*** use char arrays like that in C++.  Use std::string.

No point in talking about your code until you fix that.  There's also no need to create a class like you did.  If you want a class to represent a password, just have store the password and compare the strings.  Don't have it prompting for the input like that, it's really beyond it's scope.

---

### Post by thumper on 2006-08-18
I have a very similar response to that of **LordHunter317**.

I quickly read the post and went "NOOOO!!!!! don't do that", but then I read said previous post and thought "sanity reigns again".

---

