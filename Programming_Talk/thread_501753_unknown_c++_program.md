---
title: "unknown c++ program"
date: 2007-07-15
forum: Programming Talk
---

### Post by zerobinary on 2007-07-15
i motify someone script and the script just display random numbers 
```
#include <iostream>
using namespace std;

int main()
{
int t, count;

for(t=0;; t++) {
count = 1;
for(;;count++) {
cout <<count<< ' ';
if(count==10) break;
} 
```
i want to know what is the function of that script
```

#include <iostream>
#include <string>
using namespace std;
int main (){
cout<<"guess my name"<<endl;
string name;
const::cin>>name;
if (name==zerobinary) {//lol my first program plz give me some suggestion
cout<<"you are right!!"<<endl;
{else //action if u a wrong
cout<<"guess again"<<endl;
}
}
return 0;
}
//haven't compile it yet but plz give me some suggestion is my first program

```

---

### Post by aks44 on 2007-07-15
> **zerobinary said:**
> //haven't compile it yet but plz give me some suggestion is my first program

As a suggestion: always compile your programs before posting, to make sure that they contain no syntax errors.
Also indent your code, it is totally unreadable as it is.

---

### Post by zerobinary on 2007-07-15
still how about the first app
and i did indent my code

---

### Post by aks44 on 2007-07-15
> **zerobinary said:**
> still how about the first app

Well it doesn't compile, so I can't say for sure. (call me picky on this one :p)

*If* it didn't contain any syntax error, it would supposedly print numbers from 1 to 10, start over at 1 etc until you kill the app, there is a power outage, men destroy the earth or the universe collapses, whichever comes first.

> **zerobinary said:**
> and i did indent my code
Sorry but it doesn't look indented here...

---

### Post by zerobinary on 2007-07-15
indent can u give me an example of what kind of indent a u talking about
and won't compile what mistake did i make crying my first c++ cpp i make fail
is there a way to fix it

---

### Post by Paul820 on 2007-07-15
This is proper indenting, plenty of spaces around operators, use tabs of four or four spaces whichever you want. I use a tab size of four replaced with spaces. Code is supposed to flow in and then out to make it easier for others, and yourself to read. You first program will never exit as you have count = 1 inside the loop. Each iteration through the loop sets count back to one again so if count == 10 will never be true. You have an infinite loop.

```
#include <iostream>
#include <string>

using namespace std;

int main()
{
    cout << "guess my name" << endl;
    string name;
    cin >> name; // Removed the const

    if ( name == "zerobinary"  ) // Quotes around zerobinary were missing
        cout << "you are right!!" << endl;
    else //action if u a wrong
        cout << "guess again" << endl;

    return 0;
}

```

---

### Post by zerobinary on 2007-07-15
how about the one i create will it work 
```
#include <iostream>
#include <string>

using namespace std;

int main()
{
    cout << "guess my name" << endl;
    string name;
    cin >> name; // Removed the const

    if ( name == "zerobinary"  ) // Quotes around zerobinary were missing
        cout << "you are right!!" << endl;
{
    else //action if u a wrong
        cout << "guess again" << endl;
}//do u need this curved blanket there
    return 0;
}

```

---

### Post by aks44 on 2007-07-15
Here's the first code snippet, both corrected to be compilable and also indented:

```
#include <iostream>
using namespace std;

int main()
{
    int t, count;

    for (t = 0; ; t++)
    {
        count = 1;
        for ( ; ; count++)
        {
            cout << count << ' ';
            if (count == 10) break;
        }
    } // you forgot to close that brace
    return 0; // you forgot to return a value from main()
} // you forgot that brace too
```

"indentation" is the fact of putting spaces in front of a line, in order to have the blocks of code visibly separated according to their nesting level.


A few remarks:
- **using namespace std;** is generally regarded as bad form.
- if you don't need a variable outside a **for** loop, declare it in the **for** definition to avoid cluttering your code. Both your variables **t** and **count** are concerned.
- The breaking condition **if (count == 10) break;** could be also put in the **for** definition, it would be much cleaner.
- Breaking conditions should use < or <= when possible rather than == or != as this tends to make the code more robust.
- A **for** loop without condition is generally better represented using some other kind of loop. BTW, you don't make any use of the **t** variable, so it is useless. The outermost **for** loop can thus be rewritten as a **while (true)** loop.

IOW your code could be rewritten as:

```
#include <iostream>

int main()
{
    while (true)
    {
        for (int count = 1; count <= 10; ++count)
        {
            std::cout << count << ' ';
        }
    }
    return 0;
}
```

Which leads us to notice that you're doing an infinite loop...

---

### Post by zerobinary on 2007-07-15
thx but how about the app the one i created 
```
#include <iostream>
#include <string>

using namespace std;

int main()
{
    cout << "guess my name" << endl;
    string name;
    cin >> name; 

    if ( name == "zerobinary"  ) // Quotes around zerobinary were missing
        cout << "you are right!!" << endl;

    else //action if u a wrong
        cout << "guess again" << endl;

    return 0;
}
```
> how come this won't repeat it subpose to be infinate loop
or should i use while statement
```
 while (name !="zerobinary")
{
cout<<"guess again"<<endl;
if (name="zerobinary")
cout<<"you are right"<<endl;
}

```
first app it work just that i want to know what is the function now i know it that one is fixed
> - using namespace std; is generally regarded as bad form.why isn't that short form for std::cout and those stuff 
isn't it making life easier

---

### Post by AlexThomson_NZ on 2007-07-15
```

#include <iostream>
#include <string>

using namespace std;

int main()
{
    string name;
    bool guessing=true;
    
    cout << "guess my name" << endl;
    
    while (guessing)
    {
        cin >> name; 

        if ( name == "zerobinary"  )
        {
            /* User guessed correctly */
            cout << "you are right!!" << endl;
            guessing = false;   
        } 
        else
        {            
            /* User guessed wrong */
            cout << "guess again" << endl;
        }
    }

    return 0;
}

```

---

### Post by zerobinary on 2007-07-15
>     bool guessing=true; what does that lines mean
```

*/is there a way to turn this app to a active background for desktop
like a gif desktop background 
except the numbers change 
and the numbers color change into green like the one in martaix
if this is impossible i am sorry
/*


#include <iostream>
using namespace std;

int main()
{
int t, count;

for(t=0;; t++) {
count = 1;
for(;;count++) {
cout <<count<< ' ';
if(count==10) break;
}

}
}

```

---

### Post by Modred on 2007-07-16
Your posts give me headaches.  But I'll attempt to help anyway.

> bool guessing=true; what does that lines mean
He creates a variable of type **bool**, calls it **guessing**, and initializes it to **true**.  Tada.  A boolean data type can only hold two values, true or false.

Later in the program he uses it as a sentinel to control the loop.  If the person guesses incorerctly, he prints the error message and then the loop continues.  Because guessing is still true, the while condition evaluates to true and the loop executes again.  When the user guesses correctly, guessing is set to false, so on the next test of the while loop the condition fails and the loop exits.

Also, comments are /* */ and not */ /*.

---

### Post by Wybiral on 2007-07-16
I still think C is easier for beginners then C++...

---

### Post by aks44 on 2007-07-16
> **zerobinary said:**
> why isn't that short form for std::cout and those stuff isn't it making life easier

See that post : [http://ubuntuforums.org/showthread.php?p=3027407#post3027407](http://ubuntuforums.org/showthread.php?p=3027407#post3027407)

---

### Post by zerobinary on 2007-07-16
just in response to wybiral well 
because most people say c is pretty much die not c# so i learn c++ and they say is easier adn is too late to switch since i learn half way

---

