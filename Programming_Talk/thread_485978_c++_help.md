---
title: "c++ help"
date: 2007-06-27
forum: Programming Talk
---

### Post by zerobinary on 2007-06-27
```
#include <iostream>
#include <string>
int main()
{
std::cout<<"plz enter ur name: ";
std::string name; // some of the space is not right but is ok
std::cin>>name;// don't know if u need the space between cin>> and name
const std::string greeting = "hello, "+ name + "!";
const std::string spaces(greeting.size(), ' ');
constd std::string second = "* " + space + " *";
constd std::string first (second.size(), '*');
std::cout<< std::endl;
std::cout<<first<<std::endl;
std::cout<<second<<std::endl;
std::cout<<first<<std::endl;
return0;
}

```
need help can const std::string spaces(greeting.size(), ' '); be constd std::string spaces=greeting.size(),' '
and what is the difference between making a valuable with = and blackets
and i don't want to make a new topic so i am just going to combine both c++ question into one
```
#include <iostream>
#include <string>
using namespace std;
int main()
{
string anime;
std::cout<< "Please enter ur name: '\n'";
cin>>anime;
std::cout<<"hello,"+anime+"!" <<std::endl;
return 0;
}

```
```
how come the result is this 
Please enter ur name: '
'
```
i want to get rid of the ' ' in the output

---

### Post by Modred on 2007-06-27
For the second problem, you don't need to put single quotes around the newline esape character.  Because it's in a string, you can just put the \n.

```
std::cout << "Please enter your name:\n";
```

That will give:
**Please enter your name:**
<cursor here>

---

### Post by zerobinary on 2007-06-27
thx but does anyone have an answer to that
```
#include <iostream>
#include <string>
int main()
{
std::cout<<"plz enter ur name: ";
std::string name; 
std::cin>>name;
const std::string greeting = "hello, "+ name + "!";
const std::string space(greeting.size(), ' ');
const std::string second = "* " + space + " *";
const std::string first (second.size(), '*');
std::cout<<std::endl;
std::cout<<first<<std::endl;
std::cout<<second<<std::endl;
std::cout<<first<<std::endl;
return 0;
}
```

need help can const std::string spaces(greeting.size(), ' '); be constd std::string spaces=greeting.size(),' '
and what is the difference between making a valuable with = and blackets
how come the output is plz enter ur name: sucker

******************
*                *
******************

not ******************
    *   sucker         *
     ******************
or something like that at least according to accelerated c++ page 12

---

### Post by natez0r on 2007-06-27
> **zerobinary said:**
> thx but does anyone have an answer to that
```
#include <iostream>
#include <string>
int main()
{
std::cout<<"plz enter ur name: ";
std::string name; // some of the space is not right but is ok
std::cin>>name;// don't know if u need the space between cin>> and name
const std::string greeting = "hello, "+ name + "!";
const std::string spaces(greeting.size(), ' ');
constd std::string second = "* " + space + " *";
constd std::string first (second.size(), '*');
std::cout<< std::endl;
std::cout<<first<<std::endl;
std::cout<<second<<std::endl;
std::cout<<first<<std::endl;
return0;
}
```

need help can const std::string spaces(greeting.size(), ' '); be constd std::string spaces=greeting.size(),' '
and what is the difference between making a valuable with = and blackets

I cannot understand your wording of the question, could you rephrase? (I may not be the best C++ resource, since i haven't used it in awhile but I'm sure the clarification would help the eventual answer come out)

---

### Post by Soybean on 2007-06-27
> **zerobinary said:**
> 
need help can const std::string spaces(greeting.size(), ' '); be constd std::string spaces=greeting.size(),' '

Nope. 

> 
and what is the difference between making a valuable with = and blackets


When you use =, you're assigning a value to a variable that already exists. For example,
```
int a=10;
```
is equivalent to
```
int a;
a = 10;
```

With the brackets, you're initializing the std::string using its constructor function. That is, the std::string is created, and its value is set, all at once. There are ways to assign a value to a std::string using =, but they're all slower, since the std::string is first created and assigned a default value, THEN given the value you want it to have (i.e. its value gets set twice).

---

### Post by zerobinary on 2007-06-27
so you can use = but it will be slower in that case
second of all how come the result is this  
****************
*              *
****************
 not with the name inside the border
and 
> There are ways to assign a value to a std::string using =, but they're all slower
how do u do that anyways since i am eagar to learn
one more question is const std::string message=hello +",world"+ "!";
and const std::string mesage = "hello"+",world" +exclam valid statement 
just want t make sure 
personally i think no
thx for the help u guys have offer me

---

### Post by Soybean on 2007-06-27
> **zerobinary said:**
> not with the name inside the border
Try changing 

```
std::cout<<second<<std::endl;
```

to

```
std::cout<<greeting<<std::endl;
```

and see if it does what you want. I'm not 100% sure what you're trying to do there, but this seems worth a shot. ;)

---

### Post by Paul820 on 2007-06-27
I don't think he has put all the code in. In my book ( Accelerted C++ ) it is this:

```
#include <iostream>
#include <string>

int main()
{
    std::cout << "Please enter your first name: ";
    std::string name; 
    std::cin >> name;
    
    const std::string greeting = "hello, "+ name + "!";
    const std::string space(greeting.size(), ' ');
    const std::string second = "* " + space + " *";
    const std::string first(second.size(), '*');

    std::cout << std::endl;
    std::cout << first << std::endl;
    std::cout << second << std::endl;
    std::cout << "* " << greeting << " *" << std::endl;
    std::cout << second << std::endl; 
    std::cout << first << std::endl;
    
    return 0;
}
```

const std::string space( greeting.size(), ' ' );

is saying you want to reserve enough space in the string equal to the size of greeting and fill it with spaces.

---

### Post by zerobinary on 2007-06-27
> Soybean say
There are ways to assign a value to a std::string using =, but they're all slower
and is const std::string message=hello +",world"+ "!";
and const std::string mesage = "hello"+",world" +exclam valid statement
and what is the difference between a string and string literal 
and one more quick thing in accelerated c++ page 14-15section 1.3 detail 
i don't quite get what do they mean by os<<os writes the character contained in s, without any formatting changes, on the output stream denoted by os the result of the expression is os
and the explanation for is>>s reads and discards characters from the stream, demoted by os until encounter a character that is not whitespace then read successive characters from is into s overwriting whatever value s might have had until the next character read would be whitespace the result is is

---

### Post by Modred on 2007-06-29
> **zerobinary said:**
> and is const std::string message=hello +",world"+ "!";
and const std::string mesage = "hello"+",world" +exclam valid statement
and what is the difference between a string and string literal 
and one more quick thing in accelerated c++ page 14-15section 1.3 detail 
i don't quite get what do they mean by os<<os writes the character contained in s, without any formatting changes, on the output stream denoted by os the result of the expression is os
and the explanation for is>>s reads and discards characters from the stream, demoted by os until encounter a character that is not whitespace then read successive characters from is into s overwriting whatever value s might have had until the next character read would be whitespace the result is is

If hello is a string, then you can do the first assignment.  But the second one will fail because it will treat the "hello" and ",world" as C style strings, which do not work with the + operator.  To be safe, I'd say you should always make sure that you are adding the quoted parts to a string object and not just another set of chars.  Of course, after you assign these to a constant variable, you won't be able to change that variable.

A string literal is a bit of text you have hard coded into the code.  In your questions, "hello" is a string literal.

```
os << s;
```
This is more or less the same as "cout << s;", except you are using a different output stream (or at least a different reference to the stream referenced by cout).   The reason it returns an output stream is so that you can chain them together:

```
cout << s << "a string literal" << endl << "blah blah" << endl;
```
If it did not return a reference to the output stream, then this code would not compile because after the first link in the chain was processed, there would be no stream for the others pieces to use.

```
is >> s;
```
Is the same as using "cin >> s;" from within your main.  Of course, your input stream could be several different things (a reference to cin, a reference to a file, etc), but it works more or less the same regardless.

---

