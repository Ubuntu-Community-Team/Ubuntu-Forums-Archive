---
title: "C++: Unknown problem"
date: 2010-10-19
forum: Programming Talk
---

### Post by fallenshadow on 2010-10-19
Ok this program is relatively simple and some people have already seen it. However I am having huge problems with it and I don't know why.

Basically this program is supposed to accept a string into an array of strings. Then different functions will allow you to manipulate those strings.

The problem I have is I can input a string but when I try to print the list of strings (codes) it fails. I had a colleague of mine look over my code in class but he couldn't figure it out either.

All I want is for people to look over this pretty simple program and tell me where the problem is. Please help! I am already waaay behind in C++ exercises we are meant to do. 

NOTE: its uploaded as a .txt but can be copied and pasted into any editor of your choice! :)

---

### Post by dwhitney67 on 2010-10-19
Well, since you did not post your code, here's how I would have done it.

```

#include <string>
#include <vector>
#include <iterator>
#include <iostream>

int main()
{
   using namespace std;

   vector<string> theWords;

   for (int i = 0; i < 5; ++i)
   {
      cout << "Enter "
           << (i == 0 ? "a" : "another")
           << " word: ";

      cin >> word;

      theWords.push_back(word);
   }

   copy(theWords.begin(), theWords.end(), ostream_iterator<string>(cout, " "));
}

```
I won't provide the code to manipulate the strings, for that is without a doubt a classroom (ie HOMEWORK) exercise.

---

### Post by fallenshadow on 2010-10-19
Thanks for trying to help dwhitney but maybe I should have stated it can't use anything like vectors only basic arrays.

Sorry I posted the thread and then realised I didn't upload the file. :redface:

I basically need to find whats wrong with my existing code. This problem is holding me back and ive already wasted about 10+ hours trying different things to find a problem. I can't afford to waste more time being stuck.

---

### Post by GeneralZod on 2010-10-19
You're wiping out codearray each time through the do ... while in main() (by re-defining it).

Move the 

```

string codearray[20];

```

so that it is before the "do".

---

### Post by fallenshadow on 2010-10-19
Ah, I actually came across that today.. fixed it :)

Now the problem I am having is.. I enter a code and then another code but the result is like this:

String 1: code1
String 2: code1code2

Hmm... not sure what is going on here but I will have another look at my code tonight.

EDIT: Fixed that... now the code is assembled properly! :) Woot!
EDIT2: Also fixed the printing of the function as a result of fixing code assembly!! LOL :D

I guess I can consider this thread solved! Don't know why I posted but at the time I was desperate for help.

---

