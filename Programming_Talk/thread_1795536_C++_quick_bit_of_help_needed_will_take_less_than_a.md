---
title: "C++ quick bit of help needed will take less than a minute i promise!"
date: 2011-07-02
forum: Programming Talk
---

### Post by TomAnkcorn on 2011-07-02
```
#include <iostream>
 
using namespace std;
 
int main()
{
 
 int age = ( 2011 - dob ); //its something to do with this what am i doing wrong?
 int dob;
 
 cout<<"please enter your date of birth: ";
 cin>> dob;
 cin.ignore();
 
 if ( age < 100 ){
         cout<<"you are young!\n";
        }
        else if ( age == 100 ) {
                cout<<"you are old!\n";
}
        else {
                cout<<"you are really old!\n";
        }
 cin.get();
}
```

not quite sure what i am doing there just following tutorials and trying to change stuff as i go. need help about line 8

---

### Post by cgroza on 2011-07-02
You are using the dob variable before even declaring it and initializing it.

Moving line 8 after cin.ignore() will most likely solve your problem.

---

### Post by TomAnkcorn on 2011-07-02
yeah that solves it :P
was it messing up because its was trying to find the age before you had given it a value for dob before?

Thanks anyway

---

### Post by andrew1992 on 2011-07-03
The problem with that is that you tried to use "dob" in an expression *before* it was even defined, so the compiler of course can't know what to do with it.

---

### Post by unknownPoster on 2011-07-03
This also introduces a topic worth mentioning. Exception Handling.

Consider what happens if someone enters any of the following as input: negative numbers, non-numerical text, or nothing at all (user just presses enter). It's up to the programmer to determine how these events should be dealt with.

---

### Post by zobayer1 on 2011-07-03
This code looks more like a tutorial piece from some book or similar... May be it will include exception handling later....

@[TomAnkcorn]("http://ubuntuforums.org/member.php?u=1195499"), please mark the thread solved when your problem is solved, you will find that option in 'Thread Tools' just above your first post.

---

### Post by unknownPoster on 2011-07-03
> **zobayer1 said:**
> This code looks more like a tutorial piece from some book or similar... May be it will include exception handling later....

I would like to think that any good tutorial would recommend and/or enforce variable initialization before use in order to prevent undefined behavior, but then again, there are lots of self-proclaimed experts on the internet.

---

### Post by unknownPoster on 2011-07-03
> **zobayer1 said:**
> 
@[TomAnkcorn]("http://ubuntuforums.org/member.php?u=1195499"), please mark the thread solved when your problem is solved, you will find that option in 'Thread Tools' just above your first post.

You can't mark threads as solved any more. They removed that feature months ago. But that's off-topic.

---

### Post by zobayer1 on 2011-07-03
> **unknownPoster said:**
> I would like to think that any good tutorial would recommend and/or enforce variable initialization before use in order to prevent undefined behavior, but then again, there are lots of self-proclaimed experts on the internet.

I was talking about that without the errors, regarding the simplicity of the program, may be this is some exercise or so..

---

### Post by zobayer1 on 2011-07-03
> **unknownPoster said:**
> You can't mark threads as solved any more. They removed that feature months ago. But that's off-topic.

Are you sure about what are you talking? I marked one of my threads "SOLVED" last night... :P

---

