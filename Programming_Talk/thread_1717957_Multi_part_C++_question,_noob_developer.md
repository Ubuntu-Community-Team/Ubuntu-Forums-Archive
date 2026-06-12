---
title: "Multi part C++ question, noob developer"
date: 2011-03-30
forum: Programming Talk
---

### Post by u-noob-tu on 2011-03-30
hey guys,

i just started out learning c++ about a week ago, and im really enjoying it. but ive got a problem with all of my programs suddenly, and i dont understand what the error is telling me. heres a small program i wrote. nothing huge, just a very small start. ```
#include <iostream>
#include <stdio.h>
using namespace std;
int main()
{
int answer;
cout << "How old are you?";
cin >> answer;
switch (answer)
{
case 17:
cout << "Punk...";
break;
case 20:
cout << "One more year to go until you can get wasted legally";
}
cout << "\nPress ENTER to continue..." << endl;
cin.get();
return 0;
}
```
the strange part is that up until yesterday, i think, programs similar to this one (simple type and get reply kind of programs) would work fine, on Anjuta and codelite. i only encountered the problem when i tried Eclipse to write a slightly more complex program (which i deleted in frustration). now i get the same error on all 3 IDE's. the error is this: ```
main.cc:30: error: invalid conversion from &#8216;const char*&#8217; to &#8216;int&#8217;
```. i have no idea what that means, and as far as i can tell, the programs are identical to the ones i made a few days ago (the ones that worked). google yielded nothing useful (everybody makes different kinds of programs, and since im a noob, i cant read them and just figure it out). 

my second question is about adding libraries, specifically GTK+, to a source code file. im not quite i did it right, plus im not sure how to test that i did. ive got the dev files for GTK-2 and GTKMM, but i dont know what to do with them.

my last question is about interface design. #1 i dont know where to start #2 i dont know how to get my code to integrate into the interface #3 I have GLADE interface design, but it confuses me on what can be done with each window and buttons. couldnt find any guides on google, and the C++ books i have are beginner level, and only mention it briefly. any guides would be very appreciated.

thanks for the help.

---

### Post by d3v1150m471c on 2011-03-30
C/C++ store variable types as integers, which will be numerical variables only, char which are a single character, strings which contain well....strings, and then you have your floats. the compiler is basically trying to tell you that you're trying to convert a char variable to an integer ie you're trying to make "pizza" into "62". you have to use the proper type or convert it.

---

### Post by KonfuseKitty on 2011-03-30
For an excellent, relatively easy and quite thorough intro to Glade, this has to be the best tutorial by far:
 
tadeboro.blogspot.com/2009/09/glade3-tutorial-1-introduction.html

---

### Post by u-noob-tu on 2011-03-30
> **d3v1150m471c said:**
> C/C++ store variable types as integers, which will be numerical variables only, char which are a single character, strings which contain well....strings, and then you have your floats. the compiler is basically trying to tell you that you're trying to convert a char variable to an integer ie you're trying to make "pizza" into "62". you have to use the proper type or convert it.

seems i missed the right word for declaring a non numeric variable. what is the correct way to do it? isnt it "string *variable*"?

---

### Post by WinterMadness on 2011-03-30
in order to use the string datatype youll need:

#include <string.h>

then yes, its string variablenamehere

---

### Post by SledgeHammer_999 on 2011-03-30
```
#include <string> 
//no .h in the include

std::string my_string("Some text");
std::string my_string1;


```

---

### Post by cgroza on 2011-03-30
Also, you do not need stdio.h in that file, that is iostream for.

---

### Post by u-noob-tu on 2011-03-31
i think i may have overloaded my brain with c++, because i cant seem to make a working program now. i got the "string variable" to work, but the program isnt running correctly and i cant figure out why not. heres my little program: ```
#include <iostream>
#include <string>
using namespace std;
int main()
{
    std::string answer;
    std::string answer1;
    cout << "Please enter your name\n";
    cin >> answer;
    if ("Ryan");
    {
        cout << "Welcome, Ryan. I have prepared Firefox for you and opened a\n";
        cout << "\nterminal to compile your programs as well" << endl;
    }
    cout << "\nPress ENTER to continue..." << endl;
    cin.get();
    return 0;
}
```

ive been reading so much on C++ that i cant remember the most important stuff. :P

---

### Post by andrew1992 on 2011-03-31
> ive been reading so much on C++ that i cant remember the most important stuff. :razz:
While that's great that you're very dedicated to learning, maybe you should slow down and take smaller steps :)  

One problem I can see right away is that your first if statement simply says "if ("Ryan")".  There should not be a semicolon after this, as semicolons should only be used for statements.  Then, if **what** is equal to "Ryan".  if ("Ryan") will always evaluate to True.

---

### Post by u-noob-tu on 2011-03-31
thanks for the quick reply. but now i think i have a variable issue. i get this error message: ```
main.cc:29: error: could not convert ‘answer.std::basic_string<_CharT, _Traits, _Alloc>::operator= [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>](((const char*)"Ryan"))’ to ‘bool’
``` i think i didnt declare the variable correctly.

---

### Post by andrew1992 on 2011-03-31
Can you post your updated code? Looks like a string comparison issue.

---

### Post by muteXe on 2011-03-31
You need the if statement to look like this:

```

    if (answer == "Ryan")
    {
        cout << "Welcome, Ryan. I have prepared Firefox for you and opened a\n";
        cout << "\nterminal to compile your programs as well" << endl;
    }


```

OR 

```

    if (answer.compare("Ryan") == 0 )
    {
        cout << "Welcome, Ryan. I have prepared Firefox for you and opened a\n";
        cout << "\nterminal to compile your programs as well" << endl;
    }


```

---

### Post by safarin on 2011-03-31
> **u-noob-tu said:**
> thanks for the quick reply. but now i think i have a variable issue. i get this error message: ```
main.cc:29: error: could not convert ‘answer.std::basic_string<_CharT, _Traits, _Alloc>::operator= [with _CharT = char, _Traits = std::char_traits<char>, _Alloc = std::allocator<char>](((const char*)"Ryan"))’ to ‘bool’
``` i think i didnt declare the variable correctly.

I try to compile your code.. seem no problem. But your code only consisted 19 lines. How come the error at 29??

you only need to change to

```

if (answer == "Ryan")

```

maybe you should update your compiler.. 
have you install gnome-core-devel?

---

### Post by u-noob-tu on 2011-03-31
> **safarin said:**
> I try to compile your code.. seem no problem. But your code only consisted 19 lines. How come the error at 29??

you only need to change to

```

if (answer == "Ryan")

```maybe you should update your compiler.. 
have you install gnome-core-devel?

the error at 29 may be because i had written a longer program and just erased everything. weird, though, because there is no longer anything at line 29.  yeah, the double "=" seems to have solved my problem. and thanks for the gnome-core-devel tip. lots of developing goodies.

---

### Post by safarin on 2011-03-31
> **u-noob-tu said:**
> the error at 29 may be because i had written a longer program and just erased everything. weird, though, because there is no longer anything at line 29.  yeah, the double "=" seems to have solved my problem. and thanks for the gnome-core-devel tip. lots of developing goodies.

No problem.. I also just learn C++ within this week. Your problem could help me too.. :popcorn:

---

### Post by SledgeHammer_999 on 2011-03-31
> **u-noob-tu said:**
> the error at 29 may be because i had written a longer program and just erased everything. weird, though, because there is no longer anything at line 29.  yeah, the double "=" seems to have solved my problem. and thanks for the gnome-core-devel tip. lots of developing goodies.

Well it wasn't only the '='. In every situation where evaluation is needed (if statements, for loops, while loops, do-while loops) you need to COMPARE a variable to another variable OR a variable to a constant. In your code you didn't compare your constant ("Ryan") to a string variable.

---

