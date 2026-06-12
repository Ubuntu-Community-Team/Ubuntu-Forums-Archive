---
title: "Executing functions C++"
date: 2010-10-11
forum: Programming Talk
---

### Post by fallenshadow on 2010-10-11
I really hate asking about such basic things but the thing is I never learn't the basics that well yet.

I have a function which I am attempting to execute while passing variables.(I can execute normal functions but am having trouble with this)

It seems to skip over this function for some reason or another.

```
string Addnewflight(string code, string codearray[], int & index);
```

Any ideas?

Im sorry to bother ye guys... yet again!

---

### Post by Tony Flury on 2010-10-11
Post all your code - or even better - cut it down to something more simple.

---

### Post by dwhitney67 on 2010-10-11
> **fallenshadow said:**
> 
I have a function which I am attempting to execute while passing variables.(I can execute normal functions but am having trouble with this)


Here is three example of calling functions (err, methods).  I'm not sure what you mean by "regular" functions, but I think it's the non-class type.
```

#include <string>

class Foo
{
public:
   void functionOne(std::string codeArray[]) {}

   static void functionTwo(std::string codeArray[]) {}
};

// free-floating function, that is only accessible within this module.
static void function(std::string codeArray[])
{
}

int main()
{
   std::string array[10];

   // call "regular" function
   function(array);

   Foo f;
   f.functionOne(array);

   // No need to use Foo object; this method is statically declared.
   Foo::functionTwo(array);

   return 0;
}

```

P.S.  In C++, when you require an array of "something", your first thoughts should always be to consider using the STL vector.

---

### Post by TheBuzzSaw on 2010-10-11
> **dwhitney67 said:**
> P.S.  In C++, when you require an array of "something", your first thoughts should always be to consider using the STL vector.

I strongly disagree with this notion, but it's not the worst advice in the world. :)

---

### Post by dwhitney67 on 2010-10-11
> **TheBuzzSaw said:**
> I strongly disagree with this notion...
Care to share your reasons for this opinion?

---

### Post by Vox754 on 2010-10-11
> **dwhitney67 said:**
> Care to share your reasons for this opinion?

OMG! I'm having the worst flashback ever!

> **akvino said:**
> Why do you suggest use of vectors over use of array? Vector has way more overhead than array. If anything Vector usage should be determined on its application/performance requirements, otherwise it's better to use arrays. :-\"

Don't go there, it's 37 posts of arguing that a vector is better in general than a micro-managed array.

---

### Post by TheBuzzSaw on 2010-10-12
> **dwhitney67 said:**
> Care to share your reasons for this opinion?

Admittedly, I come from a biased background: game development. I only ever come near vectors if I absolutely need the mechanics it offers: the ability to automatically grow with the use of push_back calls. Otherwise, I use exclusively arrays. For more business-oriented applications, it's probably smarter to use vectors... though it's probably smarter to use a more business-oriented language such as Java or C#. :)

Keep in mind that my design is usually clean enough to where I never need to pass around an array pointer *and* its size. Vectors do introduce some needless overhead, but they're not really slow either **if the programmer knows how to do a pass-by-reference**.

---

### Post by unknownPoster on 2010-10-12
> **TheBuzzSaw said:**
> 

Keep in mind that my design is usually clean enough to where I never need to pass around an array pointer *and* its size. Vectors do introduce some needless overhead, but they're not really slow either **if the programmer knows how to do a pass-by-reference**.

So you should be blaming the programmer, not the tool. Just because someone doesn't know how to use them doesn't make them a bad tool. 

The only problem that I can actually see with C++ vector is that they grow fairly quickly. See the following:

```

#include <iostream>
#include <vector>

using namespace std;

int main(){

        vector<int> d;
        for(int i = 0; i < 10; ++i){
                d.push_back(i);
                cout << d.capacity() << endl;
        }
        return 0;
};

```

Output:
```

Jeremiah-Yongues-MacBook-Pro:~ jeremiah$ vim vector.cpp
Jeremiah-Yongues-MacBook-Pro:~ jeremiah$ g++ vector.cpp 
Jeremiah-Yongues-MacBook-Pro:~ jeremiah$ ./a.out 
1
2
4
4
8
8
8
8
16
16

```

When space for the vector is reallocated, all of the existing elements are typically copied to a new memory location.Now this isn't a huge problem with vectors of ints or other "small" datatypes. However, if the vector is of user-defined objects. The memory allocation and copying can get out of hand quickly.

P.S. I'm just a senior in Computer Science, so my understanding of this could be wrong. There are many people here that are more qualified than I am that may be able to correct me or add more information.

---

### Post by dwhitney67 on 2010-10-12
> **unknownPoster said:**
> 
When space for the vector is reallocated, all of the existing elements are typically copied to a new memory location.Now this isn't a huge problem with vectors of ints or other "small" datatypes. However, if the vector is of user-defined objects. The memory allocation and copying can get out of hand quickly.

P.S. I'm just a senior in Computer Science, so my understanding of this could be wrong. There are many people here that are more qualified than I am that may be able to correct me or add more information.

Your understanding is correct; however I do not see how this would be any different if you dealt with a regular array.  Remember... your supposition is that the vector, or in the case of an array, will grow over the course of time.

Consider the effort of reallocating an array to contain one additional element, and the effort (done by the system library) of recopying the pre-existing elements/objects.

Some fodder for thought:

1.  Avoid passing STL containers by value; pass by reference instead.

2.  STL containers allocate off of the heap, not the stack.

3.  With the STL vector, the application developer can specify the size of the vector, either via the constructor or using the resize() method.  This is very similar to declaring a fixed-sized array!

---

### Post by unknownPoster on 2010-10-12
> **dwhitney67 said:**
> 
1.  Avoid passing STL containers by value; pass by reference instead.

2.  STL containers allocate off of the heap, not the stack.

3.  With the STL vector, the application developer can specify the size of the vector, either via the constructor or using the resize() method.  This is very similar to declaring a fixed-sized array!

Right I knew that. It just didn't come out in my thoughts. :P

---

### Post by Simian Man on 2010-10-12
> **unknownPoster said:**
> The only problem that I can actually see with C++ vector is that they grow fairly quickly.

There is a trade-off between growing too quickly and growing to frequently.  Growing quickly is bad because it wastes space, but growing to frequently is bad because of the memory moves needed to grow a vector.  The STL implementors need to strike a balance.  If you know that balance is bad for a particular application, you can always use a custom allocator which allows for tuned memory allocations with the power of STL containers.

Using arrays over vectors won't magically make your code faster :).

---

### Post by unknownPoster on 2010-10-12
> **Simian Man said:**
> 

Using arrays over vectors won't magically make your code faster :).

I'm not saying it will. I use Vectors all the time. :P

---

### Post by Simian Man on 2010-10-12
> **unknownPoster said:**
> I'm not saying it will. I use Vectors all the time. :P

Sorry, that part wasn't directed at you, hence the new paragraph.

---

### Post by fallenshadow on 2010-10-12
Wow... calm down guys I don't wanna be the trigger of an argument here. :)

I finally stripped down the code to almost as small as I need to show ye. I did modify what I originally had but now ive come across another problem.

```
string.cc:83: error: cannot convert ‘std::string’ to ‘std::string*’ for argument ‘2’ to ‘void Addnewflight(std::string, std::string*)’
```

[PHP]
#include <iostream>
#include <string>

using namespace std;

string Flightcode(string source, string destination);
char DisplayMenu();
void Choice();
void Addnewflight(string code, string codearray[]);

int main()
{
    string source;
    string destination;
    string code;


//read in source & destination
    cout<<"where is the source?"<<endl;
    cin>>source;
    cout<<"where is the destination?"<<endl;
    cin>>destination;


//output code
    code =Flightcode(source, destination);
    cout<<"Your flight code is "<<code<<endl;

    DisplayMenu();
    Choice();

    return 0;

}

string Flightcode(string source, string destination)
{
    string code;

    source.assign(source,3,3);
    destination.resize (3);

    code = source+"-"+destination;

    return code;
}

char DisplayMenu()
{
    char menuValue;
    cout<<"Please select an option from the menu"<<endl;
    cout<<endl;
    cout<<"A - Add a flight"<<endl;
    cout<<"U - Update a flight"<<endl;
    cout<<"D - Delete an item from the list"<<endl;
    cout<<"P - Print the flight list"<<endl;
    cout<<endl;
    cin>>menuValue;
    cout<<endl;

    return menuValue;

}

void Choice()
{
    char menuValue;
    string code, codearray, source, destination;

    switch(menuValue)
    {
        case'A': cout<<"You selected A"<<endl;

        //pass required parameters to new addFlight function
                 code =Flightcode(source, destination);
                 Addnewflight(code, codearray); //the error relates to this line.
                 
        break;
        case'U': cout<<"You selected U"<<endl; Updateflight();
        break;
       
        case'D': cout<<"You selected D"<<endl; Deleteflight();
        break;
        
        case'P': cout<<"You selected P"<<endl; Printflight();
        break;
        
        default: cout<<"Please select a valid option"<<endl;

    }
}

void Addnewflight(string code, string codearray[])
{
    cout<<"Addnewflight function"<<endl;
}
[/PHP]

I dont get how this error has come about but hopefully somebody here does.

---

### Post by GeneralZod on 2010-10-12
```

 string code, codearray, source, destination;
...
                 Addnewflight(code, codearray); 

```
   

"codearray" is declared as a string in Choice(), not a string* as expected by Addnewflight's second parameter (the parameter string codearray[] is, perhaps rather confusingly, equivalent to the parameter string* in C++).

---

### Post by TheBuzzSaw on 2010-10-12
> **Simian Man said:**
> Using arrays over vectors won't magically make your code faster :).

WHY DID NO ONE TELL ME?

[php]
Buzz.sarcasm++;
[/php]

---

### Post by dwhitney67 on 2010-10-12
FallenShadow

Get into the habit... right now!... of passing objects to your functions by _reference_... unless you have a good reason not to.  Right now you are passing everything by value, which means that you are wasting CPU time and RAM.

If a parameter will not be modified by the function, then declare it as const.

Also, but not too important, is that 99.44% (not verified!) of all C++ programmers use a lowercase letter for the first character in their function/method names, and variable names.  For example, addNewFlight().  The use of an uppercase letter as the first character is generally used for class names.  The exception to this rule, unfortunately, is the STL and Boost libraries.

---

### Post by worksofcraft on 2010-10-12
> **dwhitney67 said:**
> 

Also, but not too important, is that 99.44% (not verified!) of all C++ programmers use a lowercase letter for the first character in their function/method names, and variable names.  For example, addNewFlight().  The use of an uppercase letter as the first character is generally used for class names.  The exception to this rule, unfortunately, is the STL and Boost libraries.

and Glib... and all the C standard library stuff.. and the stuff in Stroustrup's book... and anything that I write too :biggrin:

---

### Post by fallenshadow on 2010-10-14
Yes I do know that passing by reference is indeed better... however for the time being I just want to get things working. Afterwards I can go about fixing and cleaning up the code.

As for the function names I can do a simple find and replace to fix those.

I am still trying to get my code to compile but every time I fix something then another thing breaks.

[PHP]
void Choice()
{
    char menuValue;
    string code, source, destination, codearray[100];

    switch(menuValue)
    {
        case'A': {cout<<"You selected A"<<endl;

        //pass required parameters to new addFlight function
                 code =Flightcode(source, destination);
                 Addnewflight(code, codearray);
        break;
		}
     
        default: cout<<"Please select a valid option"<<endl;
    }
}
[/PHP]

Here is the error message:

```
string.cc:77: warning: ‘menuValue’ may be used uninitialized in this function
```

I don't really know what this error message is trying to tell me... :confused:

---

### Post by Barrucadu on 2010-10-14
You're using 'menuValue' without first giving it a value.

---

### Post by dwhitney67 on 2010-10-14
menuValue should be passed into the function as a parameter.  Do NOT make it a global variable.

---

### Post by fallenshadow on 2010-10-14
> You're using 'menuValue' without first giving it a value.

I already tried giving it an empty value like: 

```
char menuValue='';
```

Doesn't work...

Here is the latest errors after I tried passing those variables:

```
string.cc:(.text+0x17a): undefined reference to `DisplayMenu()'
string.cc:(.text+0x17f): undefined reference to `Choice()'
```

They are written in dull red which I think in Geany means they are not very bad errors at all. I think I will just upload the whole file as its confusing for people who only see snippets of code. 

Note: the extension was changed so I could upload. :)

---

### Post by dwhitney67 on 2010-10-14
You update the implementation of Choice() to accept a parameter... that's good.

Now, how 'bout updating the function prototype as well, and while you are at it, how about passing a parameter to the function when you call it from within main()!

P.S.  Don't forget to fix DisplayMenu() as well.  IMHO, this method should not accept a parameter; it should merely return one.

---

### Post by fallenshadow on 2010-10-17
I decided to get rid of the Choice() function in order to simplify my program and bring it into the main section.

However I thought all my problems would be sorted but im still suffering with this error. Is there anyway to fix this?? :confused:

Im sure this is the original error I was looking for a fix. I need to know how to fix this stupid error as its wasting my time and  causing me stress because I cant work on this program until this is sorted!!

```
string.cc:38: warning: ‘menuValue’ may be used uninitialized in this function
```

---

### Post by spjackson on 2010-10-17
> **fallenshadow said:**
> I decided to get rid of the Choice() function in order to simplify my program and bring it into the main section.

However I thought all my problems would be sorted but im still suffering with this error. Is there anyway to fix this?? :confused:

Im sure this is the original error I was looking for a fix. I need to know how to fix this stupid error as its wasting my time and  causing me stress because I cant work on this program until this is sorted!!

```
string.cc:38: warning: ‘menuValue’ may be used uninitialized in this function
```
I don't know what your code looks like now, but you had this warning in post number #19 of this thread, and in post #20, Barrucadu explained what it meant. I'll attempt to explain more explicitly.

```
void Choice()
{
    char menuValue; [COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]
```Here menuValue is "uninitialized", i.e. you have defined a new variable and have not assigned any value to it.
```
string code, source, destination, codearray[100];

    switch(menuValue)

```and here you are asking the compiler to choose a branch based on the value in menuValue which you still have not set.

Hopefully you can follow this and relate it to your current version of your code.

---

### Post by dwhitney67 on 2010-10-17
> **fallenshadow said:**
> I decided to get rid of the Choice() function in order to simplify my program and bring it into the main section.

In other words, you gave up on trying to solve the original problem you had, even though many suggestions were offered to you.  Good going!  :guitar:

Here's a simple/crude way to get you going; maybe this will offer a little enlightenment to some of the finer points of getting and handling user input, which in the case of most non-classroom exercises, is rarely ever done via direct user input.
```

#include <string>
#include <iostream>

char getUserChoice();
bool handleUserChoice(const char choice);

using namespace std;

int main()
{
   //...

   bool done = false;

   do
   {
      const char choice = getUserChoice();

      done = handleUserChoice(choice);

   } while (!done);

   cout << "Bye!" << endl;

   return 0;
}

char getUserChoice()
{
   std::string menuValue;

   cout << "\nPlease select an option from the menu:" << "\n\n"
        << "\tA - Add a flight"      << "\n"
        << "\tU - Update a flight"   << "\n"
        << "\tD - Delete a flight"   << "\n"
        << "\tP - Print flight list" << "\n\n"
        << "Choice? ";

   getline(cin, menuValue);

   return toupper(menuValue[0]);
}

bool handleUserChoice(const char choice)
{
   bool isDone = false;

   switch (choice)
   {
      case 'A':
          cout << "Option A selected." << endl;
          break;
      case 'U':
          cout << "Option U selected." << endl;
          break;
      case 'D':
          cout << "Option D selected." << endl;
          break;
      case 'P':
          cout << "Option P selected." << endl;
          break;
      case 'Q':
          isDone = true;
          break;
      default:
          cout << "Unknown option.\n" << endl;
          break;
   }

   return isDone;
}

```

---

### Post by fallenshadow on 2010-10-17
Since you made a great effort to help me out I stopped trying to take the easy way out and put my choice function back. :)

Im sorry but if something doesn't work I have a habit of trying to take the easy route to solve the problem. Its probably something to do with me not having much confidence as a programmer... yet. I am a patient person but I find that the longer it takes for me to figure out something the more stressed I become.

Anyway I know other people did give me help but I find it hard to understand and interpret things without an example in code. That seems to be the only way I learn things. My code does compile now as I implemented something similar to your example... many thanks for that! Im forever grateful! 

However as I never came across this before I would appreciate a small explanation of this line:

[PHP]return toupper(menuValue[0]);[/PHP]

I know that obviously this is returning the menuValue variable but what is the toupper part doing? and the [0]?  EDIT: Actually im pretty sure this is just converting the variable to uppercase for the menu. No need to explain it now.

---

### Post by akvino on 2010-12-17
> **Vox754 said:**
> OMG! I'm having the worst flashback ever!



Don't go there, it's 37 posts of arguing that a vector is better in general than a micro-managed array.

I am working on processing Multicast and TCP/IP feeds from the exchanges to banks/ trading companies. If you say use STL - everyone and their mother will look at you as someone that does not belong in the real time data processing. Vector declarations over Array's must be justified either by the current or future requirement. I say look at your requirements and make decision based on your requirements. Don't opt for the opinion that one glove fits all. C++ is very diverse language, it has applications everywhere, and pending on what you need it to do, chose either STL vector, or an Array.

[http://en.wikipedia.org/wiki/Vector_(C%2B%2B](http://en.wikipedia.org/wiki/Vector_(C%2B%2B))

---

### Post by dwhitney67 on 2010-12-17
> **akvino said:**
> If you say use STL - everyone and their mother will look at you as someone that does not belong in the real time data processing.

Why is this so?  If one were to declare their arrays (or say, vector) during initialization to be the appropriate size as required by the application, it shouldn't matter.

What's costly in terms of real-time programming is allocating memory during the processing of data.

I've worked both sides of the "fence" -- desktop applications, and embedded applications.  Surely your co-workers have explained to you what is good practice and what is not, and more importantly, why it is so.

---

### Post by akvino on 2010-12-23
> **dwhitney67 said:**
> Why is this so?  If one were to declare their arrays (or say, vector) during initialization to be the appropriate size as required by the application, it shouldn't matter.

What's costly in terms of real-time programming is allocating memory during the processing of data.

I've worked both sides of the "fence" -- desktop applications, and embedded applications.  Surely your co-workers have explained to you what is good practice and what is not, and more importantly, why it is so.

Allocating memory on the heap just takes to long, that's the justification. Don't use STL since STL classes will use memory on the heap and then reallocate that memory with even bigger chunks if needed. This all takes time which is wasted. Every microsecond counts. 

Now having said that - if I write a class that will parse a file and load the hash table prior to real time processing - than it is perfectly fine to use stl::string or vector.

---

