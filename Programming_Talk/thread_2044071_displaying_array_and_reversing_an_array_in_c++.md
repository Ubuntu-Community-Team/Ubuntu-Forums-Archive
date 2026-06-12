---
title: "displaying array and reversing an array in c++"
date: 2012-08-18
forum: Programming Talk
---

### Post by Crash525 on 2012-08-18
Ive tried searching this but not luck, I have done this before and I am having a complete brain fart on how to do this. I am just tinkering around with programs getting back into the swing of things. When I try to display the array with a for loop I get the whole array. If I try to display it backwards it skips the loop. The array is a set size of 50 characters. I just cannot figure out what I missing. Thanks for taking a look.

Here's the code.

```

#include <iostream>
#include <string>
using namespace std;

int main()

{

void Hello();
void Age();
void Sentence();

const int SIZE = 50;
int Word = 0;
int Length = 0;




Hello();
Age();
Sentence();

cout << endl;
cout << myString;
cout << endl << endl;

cout << "Please hit enter to exit program.";
cin.get();

return 0;

}


/***************Hello**************/

void Hello()

{

    cout<< "Hello!" << endl;
}

/***********************************/



/*************Age*****************/

void Age()
{

int age;
int i;

cout << "How old are you? " << endl;

cin >> age;

cout << "You are " << age << " years old." << endl;

for(i = 1; i <= age; ++i)
{cout << i << " ";}

cout << endl;

cin.clear();

}

/************************************/    



/***********Sentence*****************/

void Sentence()
{


const int SIZE = 50;
char sentence;
char N[SIZE];
int i = 0;

cout << "Write a sentence up to 50 characters long. --> ";

cin >> sentence;

cout << endl;

while(sentence != '\n')                
{
    N[i]=(sentence);    
    cout << N[i];
    ++i;                            
    cin.get(sentence);                    
}

cout << endl << endl;

cout << "Your sentence has " << i << " characters." << endl << endl;

for (i = 0;N[i] != '\0'; i++)
{
    cout << N[i];
}

cout << "\n\nThis is the sentence backwards.\n";

for(i = --i; N[i] == 0; i--)
{
    cout << N[i];
}

}
```

---

### Post by slooksterpsv on 2012-08-18
The only way I could get it to work was the change the last for loop to this:

for(i = i - 2; i >= 0; i--)
{
    cout << N[i];
}

The reason it doesn't work is because a for is like a while, while i >= 0 then continue the for loop. If it says while N[i] == 0 it won't work cause N[i] never equals 0.

---

### Post by dwhitney67 on 2012-08-18
> **Crash525 said:**
> I am just tinkering around 

There's nothing wrong with tinkering, however if you are trying to get back into the swing of programming, I would suggest that you learn the proper way to gather/store user input.  Using an array to store a string is unwarranted in C++.  Use the STL string instead.

For example:
```

#include <string>
#include <iostream>

int main()
{
    std::string input;

    std::cout << "Enter a long sentence: ";
    std::getline(std::cin, input);

    std::string reverseInput(input.rbegin(), input.rend());

    std::cout << "\n\n"
              << "Your sentence has " << input.size() << " characters in it.\n"
              << "This is what you entered: " << input << "\n"
              << "Here's that sentence in reverse order: " << reverseInput
              << std::endl;
}

```

---

### Post by Crash525 on 2012-08-19
I was trying to stay away from having an actual number size given in the for loop such as '2' and so on. I wanted it to be universal, but it works.

---

### Post by Crash525 on 2012-08-19
I have never messed with much of the string library. All of my previous course work had been to manipulate it on your own. Its ridiculous how much I forgot after not having wrote any program for a year or so, I feel like a beginner all over again. Thanks for the info, I will have to do some research in finding how to display it backwards and research on the library's functions. I there a way to have a loop check for a negative in a number?

---

### Post by trent.josephsen on 2012-08-20
> **Crash525 said:**
> All of my previous course work had been to manipulate it on your own.
This is a pervasive mentality in academia and quite harmful to practical programming IMO. It's better to learn a language the way it's used in real life. (One reason I really liked *Learning Perl* -- it takes real-world problems and shows you how to handle them realistically.)

---

### Post by Crash525 on 2012-08-20
I finally got it figured out but I had to change the for loop to a while  loop to do so. I could not find a universal character to terminate the  for loop the second time. With my school work I realize now that its is much harder than  it has to be. Since most everything has a specific function written I  might as well use it and not waist my time trying to figure it out on my  own.   


To note their is a word count function in here and its not being used so please ignore it.

```
#include <iostream>
#include <string>
using namespace std;

int main()

{

//int WordCount();
void Hello();
void Age();
void Sentence();



string myString = "You did it!!!!";
const int SIZE = 50;
int Word = 0;
int Length = 0;




Hello();
Age();
Sentence();

cout << endl;
cout << myString;
cout << endl << endl;

return 0;

}


/************WordCount************/

int WordCount()
{

int N[50];
int i = 0;
int Word = 0;
    
    for(i=0;N[i] != '\n';++i)
    {
        ++Word;
    }

++Word;

return Word;
}
/**********************************/




/***************Hello**************/

void Hello()

{

    cout<< "Hello World" << endl << endl;
}

/***********************************/



/*************Age*****************/

void Age()
{

int age;
int i;

cout << "How old are you? ";

cin >> age;

cout << "\nYou are " << age << " years old." << endl << endl;

for(i = 1; i <= age; ++i)
{cout << i << " ";}

cout << endl << endl;

cin.clear();

}

/************************************/    



/***********Sentence*****************/

void Sentence()
{


const int SIZE = 50;
char sentence;
char N[SIZE];
int i = 0;

cout << "Write a sentence up to 50 characters long. --> ";

cin >> sentence;

cout << endl;

while(sentence != '\n')                
{
    N[i]=(sentence);    
    //cout << N[i];
    ++i;                            
    cin.get(sentence);                    
}

cout << endl;

cout << "Your sentence has " << i << " characters." << endl;

cout << "\n\nThis is the sentence backwards.\n\n";

while(i != 0 )
{--i;
    cout << N[i];
    
}

cout << endl;

}
```

---

### Post by dwhitney67 on 2012-08-20
> **Crash525 said:**
> I finally got it figured out...  

```
#include <iostream>
...

cout << "Write a sentence up to 50 characters long. --> ";

cin >> sentence;

cout << endl;

while(sentence != '\n')                
{
    N[i]=(sentence);    
    //cout << N[i];
    ++i;                            
    cin.get(sentence);                    
}

...

```


Oftentimes, asking a user to "do this, but not this" is begging for disaster.

You should have inserted guards in your while-loop to ensure that the user does _not_ enter more than 49 characters (the 50th character needs to be reserved for the terminating null-character).

Also, ask yourself this... does N seem like a good variable name?  How about renaming it to 'sentence', and in lieu of the existing variable with that name, perhaps change it to 'ch' or 'input'.

---

### Post by Crash525 on 2012-08-21
I am starting to come back to my senses with writing programs. Its easy for me to remember what each variable name is for but that is not a good habit to pick up. Thanks for pointing that out because I did forget to add a check for to much input. 

Right now I am trying to pass an array to a function, but its not working out to well. I'm going to see if I can find the correct syntax for it before I ask for help. 

One question though, after the loop does the string stored in sentence get deleted?

>  while(sentence != '\n')                  {      N[i]=(sentence);         //cout << N[i];     ++i;                                 cin.get(sentence);                     }


---

### Post by dwhitney67 on 2012-08-21
> **Crash525 said:**
> 
One question though, after the loop does the string stored in sentence get deleted?
A variable, and its contents, will live throughout the scope in which it is declared.  Thus if you declare the array 'N' in a function, that's the scope for which is is defined.  It will not be visible outside of the function.

If however you allocate a region of space on the heap, and maintain a pointer to that region, then it can be accessed outside of the function where it was allocated.  The key is to ensure that a reference to that region is maintained at all times (otherwise you will have a memory leak).

---

### Post by Crash525 on 2012-08-21
So I should make the variable a global variable so I can use it in more than one function. I wanted to make the string sentence usable in other functions but sentence was only called in a function. Is it possible to call a function within a function? Sorry to ask instead of looking it up but it seems like I get a more detailed answer from this forum.

---

### Post by muteXe on 2012-08-21
that method is returning void at the moment, so you could make it return your sentance variable?

hold on, which variable are you talking about?

---

### Post by dwhitney67 on 2012-08-21
> **muteXe said:**
> that method is returning void at the moment, so you could make it return your sentance variable?

Exactly my thoughts.

```

int main()
{
    char* sentence = getSentence();

    function(sentence);

    delete [] sentence;
}

char* getSentence()
{
    ...
    char* sentence = new char[SIZE];

    ...

    return sentence;
}

void function(const char* sentence)
{
    ...
}

```

---

