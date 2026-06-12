---
title: "Suggestions/Hints/Difficulties about Beginners Programming Challenges."
date: 2011-05-09
forum: Programming Talk
---

### Post by leon.vitanos on 2011-05-09
Yesterday i saw the [**Beginners Team Programming Challenges Index**]("http://ubuntuforums.org/showthread.php?t=1714324") and it sound great to me.. I just finished 1st and 2nd but i would love to see some suggestions about my code ( C++ used )

So for the first one. 

```
include <iostream> using namespace std;  int main(){ int beers=99;

cout << "[Beginner] Programming Challenge: 1\n\n";
cout << "Lyrics of the song 99 Bottles of Beer\n\n"; 
while (beers>0) 
{cout << beers << " bottles of beer on the wall, " << beers << " bottles of beer.\n";
  beers -=1;  
if(beers ==0)      
cout << "Take one down and pass it around, no more bottles of beer on the wall.\n\n"; 
else  
cout << "Take one down and pass it around, " << beers << " bottles of beer on the wall.\n\n"; } 
cout << "No more bottles of beer on the wall, no more bottles of beer.\nGo to the store and buy some more, 99 bottles of beer on the wall.\n"; return 0; 
}
```and for the second one.

```
#include <iostream>
using namespace std;
#include <stdlib.h>

bool no_character(string input)
{
    for (unsigned int i=0; i < input.size(); i++)
        {
            if(isalpha(input[i]))
                return false;
        }
    return true;
}

bool space(string input)
{
    for (unsigned int i=0; i < input.size(); i++)
            {
                if(isalpha(input[i]) || isspace(input[i]))
                    return true;
            }
        return false;
}

int main(){

string name;
string input;
int age;
int userid;

cout << "[Beginner] Programming Challenge: 2\n\n";
cout << "Type exit and press enter to close this program.\n";

//NAME
cout << "Please type your name in Ubuntu forums and press enter: ";

while(true){
getline (cin, name, '\n');
if (name=="exit") return 0;
else if (name.size()==0) cout << "Your Forum's name cannot be blank, please try again: ";
else if (name[0]==' ') cout << "Your Forum's name cannot start with a space, please try again: ";
else if (no_character(name)) cout << "Your Forum's name must contain a non-numerical character, please try again: ";
else if (name.length() > 20) cout << "Your Forum's name cannot have more than 20 characters, please try again: ";
else break;}

//AGE
cout << "Please type your age and press enter: ";
while(true){
getline (cin, input, '\n');
age = atoi(input.c_str());

if (input=="exit") return 0;
else if (input[0]==' ') cout << "Your age cannot start with a space, please try again: ";
else if (input.size()==0) cout << "Your age cannot be blank, please try again: ";
else if (age < 1 ) cout << "Your age cannot be less than zero, and must be a number, please try again: ";
else break;}

//USER ID
cout << "Please type your user id and press enter: ";
while(true){
getline (cin, input, '\n');
userid = atoi(input.c_str());

if (input=="exit") return 0;
else if (space(input)) cout << "Your user id cannot include a space or letters but only numbers, please try again: ";
else if (input.size()==0) cout << "Your user id cannot be blank, please try again: ";
else if (input.size()>6 || input.size()<6) cout << "Your user id must be 6 numbers, please try again: ";
else if (userid < 1 || userid >999999) cout << "Your user id cannot be less than 1 or greater than 999999, please try again: ";

else break;}

//RESULT
cout << "\nYou are " << name << ", aged " << age <<  " next year you will be " << age+1 << ", with user id " << userid;
if (userid==999999) cout << ", you are the last user at Ubuntu Forums.\n";
else cout << ", the next user is "  << userid+1 << ".\n";
return 0;
}

```I have no errors in both of them. 

P.S At the code of the second one (!input.size()==6) wasn't working so i did it (input.size()>6 || input.size()<6). Any suggestion about that?

P.S 2 For the third one. 
What should "**out.text**" contain?

```
6. Hindi
17. Sanskrit
18. Santhali
19. Sindhi
23. English

```OR

```
1. Hindi
2. Sanskrit
3. Santhali
4. Sindhi
5. English

```

---

### Post by ziekfiguur on 2011-05-09
In the first program you print `1 bottles' where it should be '1 bottle'

In the second program you include stdlib.h, that is a C header and obsolete in C++, use #include <cstdlib>

I haven't really looked at the code for the second program, as your code is formated quite horrible.

---

### Post by leon.vitanos on 2011-05-09
> **ziekfiguur said:**
> In the first program you print `1 bottles' where it should be '1 bottle'

In the second program you include stdlib.h, that is a C header and obsolete in C++, use #include <cstdlib>

I haven't really looked at the code for the second program, as your code is formated quite horrible.

Ok i will fix the first one.
Didn't know about "cstdlib" thanks.
Why (!input.size()==6) doesn't work?
And what about the third one? What should out.txt contain at the end of the program?

---

### Post by matt_symes on 2011-05-09
Hi

Try

```
if (input.size() != 6)
```

Your first solution is crying out for recursion. I will knock one up to show you soon.

I have not had a good look at your other solutions.  I am busy at the moment.

You need to work on your formatting. When code is syntactically and semantically correct, what you have written is for the next developer (and also yourself at a later date) to read and understand what you are trying to achieve.

Kind regards

---

### Post by JupiterV2 on 2011-05-09
In the first test, you may also want to try converting the numbers (99-0) to their English equivalents (Ninety-nine through zero) for an extra challenge.

I haven't looked at your code too closely for the second challenge but my first observation is that you use two different coding styles/formats. Your functions no_character() and space() use different formatting than your main() function. You should use consistent formatting throughout your code.

---

### Post by matt_symes on 2011-05-09
Hi

Here is a recursive version of your first challange

```
#include <iostream> 

// Explictly reference from the namespace.
using std::cout;
using std::endl;

const int TotalBeer = 10; 

int BottlesOfBeer(int NumBeers)
{
    // Display number of bottles.
    cout << NumBeers << " bottles of beer on the wall, " << NumBeers << " bottles of beer." << endl;

    // Decrement the number of bottles of beer    
    --NumBeers;

    if (NumBeers == 0)
    {
        cout << "Take one down and pass it around, no more bottles of beer on the wall." << endl;
        cout << "No more bottles of beer on the wall, no more bottles of beer." << endl << "Go to the store and buy some more, 99 bottles of beer on the wall."<< endl; 
        
        return 0;    
    } 
    
    cout << "Take one down and pass it around, " << NumBeers << " bottles of beer on the wall." << endl; 

    // Recurse.
    return BottlesOfBeer(NumBeers);
} 

int main()
{ 
    // Call the recursive function..
    return BottlesOfBeer(TotalBeer);
}
```Do you find it easier to read ?

Notice i reference only the functions i want from the std namespace using the 'using' directive. Also i use std::endl as opposed to \n.

Kind regards

---

### Post by matt_symes on 2011-05-09
Hi

BTW: As you are learning programming, i want to say i think both goes are an excellent start.

Keep at it. :D

Kind regards

---

### Post by leon.vitanos on 2011-05-09
> **matt_symes said:**
> 
```
if (input.size() != 6)
```Your first solution is crying out for recursion. I will knock one up to show you soon.

Ok it works. Thanks!

> **matt_symes said:**
> 
Do you find it easier to read ?

I am not aiming to have a good formatting with comments and all that cause this it is just for me and i have no problem reading my code again..

P.S On your code i didn't really catched the return BottlesOfBeer(TotalBeer);
Why not work with a while loop?

Thanks anyway ;)

---

### Post by matt_symes on 2011-05-09
Hi

There are two solutions to this type of problem, the iterative solution and the recursive solution.

The solution you implemented was an iterative solution. Recursion is a very important concept in programming and some solutions lend themselves more succinctly to a recursive solution, especially if speed is not the prime requisite as it takes time to set up the stack frame.

I would _highly_ recommend you learn both.

A very well done, by the way, on the first and second position. =D>

If your interested, i might have some comments on your second solution. Constructive criticism only as i think you have done pretty well. :grin:
> I am not aiming to have a good formatting with comments and all that cause this it is just for me

I would suggest that is a mistake. Get into good programming habits from the start. You will not regret it later on.

Kind regards

---

### Post by ziekfiguur on 2011-05-09
The reason that (!input.size()==6) didn't work is that unary operators like ! are processed before binary operators like ==. 
The result is that if input.size() returns anything but 0, the ! will make a 0 of it and compare that to 6. If input.size() returns 0 the ! will make a 1 of it and compare that to 6.
A way to make it work is by using brackets: (!(input.size() == 6)) or like matt_symes stated (input.size() != 6)

---

### Post by leon.vitanos on 2011-05-09
Ok thanks guys

I will post back when i continue with the other two. ( I think in a month cause i have exams now. ) .. Thanks a lot! And please let me now on what should i do with the third one :mrgreen:

---

