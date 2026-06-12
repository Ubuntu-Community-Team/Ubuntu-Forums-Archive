---
title: "Help w/C++ syntax"
date: 2010-02-11
forum: Programming Talk
---

### Post by smdawson on 2010-02-11
A question in my C++ class is asking me what will be printed by the following code

```
x = 15;
x += 3;
y = ++x % 4;
z = y--;
cout << “x = “ << x << “ y = “ << y << “ z = “ << z;
```

more than anything I need to know what the operations are.
does x += 3 mean x = x + 3?

does y = ++x % 4 mean y = 1+x % 4?

does z = y-- mean z = y?

---

### Post by akvino on 2010-02-11
It is easy to test that!

Just put 
cout<<"\nx is "<<x<<endl;

---

### Post by WildeBeest on 2010-02-11
x += 3; ->  x = x +3
y = ++x % 4; -> y = (x + 1) % 4
z = y--; -> z = (y - 1)

---

### Post by dwhitney67 on 2010-02-11
> **akvino said:**
> It is easy to test that!

Just put 
cout<<"\nx is "<<x<<endl;

The OP is probably scratching his rear, and saying "Write code?  Are you crazy!"

---

### Post by Zugzwang on 2010-02-11
@OP: Look up the definitions of the operators, and you'll get to know the answer. Note that this is likely to be the purpose of this homework question. Just one Hint: WildeBeest's solution is incorrect, I'm afraid.

---

### Post by smdawson on 2010-02-11
@dwhitney67. well, that is the last time I ask for help. :???:

---

### Post by akvino on 2010-02-11
> **smdawson said:**
> well, that is the last time I ask for help. :???:

Hahaha - what we gave you is the way to troubleshoot any possible homework assignment in the future without asking us to do it for you. In essence we did not give you a meal, but thought you how to fish.

---

### Post by WildeBeest on 2010-02-11
> **Zugzwang said:**
> @OP: Look up the definitions of the operators, and you'll get to know the answer. Note that this is likely to be the purpose of this homework question. Just one Hint: WildeBeest's solution is incorrect, I'm afraid.
 
 
Youare correct I missed one.
 
z = y, y = y - 1

---

### Post by dwhitney67 on 2010-02-11
> **WildeBeest said:**
> Youare correct I missed one.
 
z = y, y = y - 1

And this one too...
```

y = ++x % 4;

```

---

### Post by dwhitney67 on 2010-02-11
> **smdawson said:**
> @dwhitney67. well, that is the last time I ask for help. :???:

Why not write yourself 10+ lines of code that duplicates what you asked?  At every stage, you could print the value of the variable and compare with your assumptions.

---

### Post by smdawson on 2010-02-11
Yeah, I guess it would be easy enough to output the variables and backtrack through the equations real quick. I just didn't want to make a mistake and continue writing correctly. Time to fish.

---

### Post by akvino on 2010-02-11
> **dwhitney67 said:**
> And this one too...
```

y = ++x % 4;

```

Not to poke to much but this is the same as

y = (1+x) % 4;

---

### Post by dwhitney67 on 2010-02-11
> **akvino said:**
> Not to poke to much but this is the same as

y = (1+x) % 4;

Yes, 'y' will have the same value regardless of which of these two operations are used:
```

y = ++x % 4

// or

y = (1 + x) % 4;

```
However, the assignment indicated that it wanted to know about all of the values:  x, y, and finally z.

Thus, the "y = (1 + x) % 4" does NOT take into account that the value of 'x' would have been incremented if "y = ++x % 4" were taken into consideration.  In conclusion, you are wrong.

---

### Post by akvino on 2010-02-11
> **dwhitney67 said:**
> Yes, 'y' will have the same value regardless of which of these two operations are used:
```

y = ++x % 4

// or

y = (1 + x) % 4;

```
However, the assignment indicated that it wanted to know about all of the values:  x, y, and finally z.

Thus, the "y = (1 + x) % 4" does NOT take into account that the value of 'x' would have been incremented if "y = ++x % 4" were taken into consideration.  In conclusion, you are wrong.

No I am not wrong. Y value is the same and he wanted to know if that expression (++x) is equal to (1 + x) which is correct.

:-)

---

### Post by DZ* on 2010-02-11
I always felt that ++,  -- operators ain't being used creatively enough

```
#include <iostream>
using namespace std;

struct X {.
 int x;.
 X () : x (0) {}.
 X& operator ++ (int) { x++; return *this; }.
 X& operator ++ () { ++x; return *this; }.
 X& operator -- (int) { x--; return *this; }.
 X& operator -- () { --x; return *this; }.
 friend ostream & operator << (ostream& os, X& x) { return (os << x.x);}
};                                
                                  
int main () {                     
  X x;.                           
  ++++++++++++++++++ x ++++++++++++++++++;.
  ------ x ------;.
  --++ x --++++;
  cout << x << "\n";.
}
```

---

### Post by dwhitney67 on 2010-02-11
> **akvino said:**
> No I am not wrong. Y value is the same and he wanted to know if that expression (++x) is equal to (1 + x) which is correct.
:-)

Yes, that is correct.  However in the context of the original question, and the response doled out by WildeBeest, it fell out of context what I was stating.  At any rate, I originally was replying to WildeBeest.

---

### Post by SledgeHammer_999 on 2010-02-11
One quick question that's been puzzling me for quite a time. I just never needed an answer for my amateurish/hobby programming fun. What is the difference between "++x" and "x++"?

---

### Post by dwhitney67 on 2010-02-11
I could give you my $0.02 worth of knowledge, but the folks that replied to this [thread]("http://stackoverflow.com/questions/2115682/pre-increment-operator-vs-post-increment-operator") already posted the relevant information you seek.

[http://stackoverflow.com/questions/2115682/pre-increment-operator-vs-post-increment-operator](http://stackoverflow.com/questions/2115682/pre-increment-operator-vs-post-increment-operator)

---

### Post by akvino on 2010-02-11
OR here


[http://ubuntuforums.org/showthread.php?t=1388284](http://ubuntuforums.org/showthread.php?t=1388284)

---

### Post by mdurham on 2010-02-12
> **WildeBeest said:**
> x += 3; ->  x = x +3
y = ++x % 4; -> y = (x + 1) % 4
z = y--; -> z = (y - 1)
I think the 3rd line is incorrect.
Should it be: z = y--; -> z = y do you think?

---

### Post by Ravenshade on 2010-02-12
++x increments before the number
x++ gets the value then increments it. 

It's like writing 1 + x, x + 1 

or at least that's what my ZNotation lecturer taught me.

---

### Post by mdurham on 2010-02-12
> **Ravenshade said:**
> ++x increments before the number
x++ gets the value then increments it. 

It's like writing 1 + x, x + 1 

or at least that's what my ZNotation lecturer taught me.
I don't quite unerstand what you are saying here. "++x increments before the number" What does that mean?
Likewise, "x++ gets the value then increments it" is a bit meaningless.

---

### Post by Ravenshade on 2010-02-12
In other words there's no difference. 

++x = 1+ x

x++ = x + 1

---

### Post by omeraygor on 2010-02-12
x = 15;
x += 3;
y = ++x % 4;
z = y--;
cout << &#8220;x = &#8220; << x << &#8220; y = &#8220; << y << &#8220; z = &#8220; << z;

x+=3;  ====> x=x+3  x=15+3=18;
y=++x % 4; ===> y=1+(x%4); 18mod(4)=2 y=1+2=3;
z=y--;  ===> z= (y=y-1); z=3-1; z=2;

so as result. when you use like this.
y = ++x % 4;
that mean is:  y=1+(x%4);
example x=18 y=3;
Otherwise
y = x++ % 4;
that mean is:  y=(x+1)%4;
example x=19 y=2;

---

### Post by Ravenshade on 2010-02-12
My idea was right, but my implementation was wrong. Omeraygor has what I was trying to say.

---

### Post by mdurham on 2010-02-12
> **Ravenshade said:**
> In other words there's no difference. 

++x = 1+ x

x++ = x + 1

So are you saying that:

x = ++y is the same as x = y++?
If so I suggest that you try it, printing the result of x. You might be surprised.

y = 10;
x = ++y;
printf("%d %d\n", x, y);

y = 10;
x = y++;
printf("%d %d\n", x, y);

---

### Post by omeraygor on 2010-02-12
i tried.

#include <stdio.h>

int main(){
int x,y;
y = 10;
x = ++y;
printf("%d %d\n", x, y);

y = 10;
x = y++;
printf("%d %d\n", x, y);

return 0;
}

result:
11 11
10 11

So there are difference...

---

### Post by mdurham on 2010-02-12
> **omeraygor said:**
> i tried.

#include <stdio.h>

int main(){
int x,y;
y = 10;
x = ++y;
printf("%d %d\n", x, y);

y = 10;
x = y++;
printf("%d %d\n", x, y);

return 0;
}

result:
11 11
10 11

So there are difference...

You are correct, there is a difference omeraygor, well done.

---

### Post by dwhitney67 on 2010-02-12
This is an example of pre-increment
```

++x

```
This is an example of post-increment:
```

x++

```
If you have statements like:
```

x = 18;
y = ++x % 4;

```
Then the result for y is 3.  WHY?  Well, first x is incremented by 1 to become 19; _then_ the modulo takes place.

For the following:
```

x = 18;
y = x++ % 4;

```
The result of y is 2.  WHY?  Well, first the modulo takes place;  _then_ the increment of x takes place.  Thus the resulting value of x is (once again) 19.

---

### Post by omeraygor on 2010-02-12
the C language has sequential structure. so. 
x = 18;
y = ++x;

increment x before assigning

1.x=18;
2.x=x+1;
3.y=x;

x = 18;
y = x++;

increment x after assigning
1.x=18;
2.y=x;
3.x=x+1;

```


#include <stdio.h>
int main(){
int x,y;
x = 18;
y = ++x;
printf("%d %d\n", x, y);

x = 18;
y = x++;
printf("%d %d\n", x, y);

return 0;
}

19 19
19 18



```

---

### Post by smdawson on 2010-02-14
not to change the subject--but, can I compile c++ programs from the terminal? Or some command window in netbeans? I was told that 
```
g++ -o filename sourcecode.cpp
```
 is the command. But I am confused about if I am using the terminal or what. Because if I use the terminal then don't I have to specify the whole path?

---

### Post by MadCow108 on 2010-02-14
if your in the same directory as the source file you don't need a path. It searches in the current directory for the file.
but of course you can use relative or absolute paths if you wish, as with every other terminal command

---

### Post by smdawson on 2010-02-16
How can I initialize a variable, ask the user a question and for input, and then have the program recognize a string of characters ( a word or two ) and then make a decision based on the answer?

Not just true or false, but if I wanted the user to choose a color and have the program recognize it like 'blue' or 'red' and then had the program execute different code based on the users input

Would the data type be string? I tried making an if/else loop where each answer would illicit a different response, but it did not work. I realize this is wrong, I'm just showing my work so someone can correct me.(kindly)
My thoughts followed these lines 
                                                 
```

#include <iostream>
using namespace std;

int main()
{
    string color1;
    string color2;
    string input1;

    color1 = "blue"
    color2 = "red"

    cout << "What is your favoite color? (red/blue)" << endl;
    cin >> input1;

    if ( input1 = color1 )
        cout << "The color of the sea." << endl;
    else if (input1 = color2 )
        cout << "The color of tomatoes."  << endl; 
    
    return 0;
}
```

---

### Post by dwhitney67 on 2010-02-16
The single-equals character is used for assigning a value; a double-equals is used for comparisons.

```

if (input == red)
{
}
else if (input == blue)
{
}
else
{
   // error
}

```

---

### Post by smdawson on 2010-02-16
Ha. I feel stupid. Thank you.

---

### Post by smdawson on 2010-02-18
If I am outputing long lines of text through 
```
cout << ".........multiple lines vertically......" << endl;
```
is there a way I can keep words from splitting up between different lines of text? Right now I am getting half of a word on a line, and then as it continues down one line the other half of the word follows. this makes for very difficult reading.

---

### Post by dwhitney67 on 2010-02-18
> **smdawson said:**
> If I am outputing long lines of text through 
```
cout << ".........multiple lines vertically......" << endl;
```
is there a way I can keep words from splitting up between different lines of text? Right now I am getting half of a word on a line, and then as it continues down one line the other half of the word follows. this makes for very difficult reading.

I'm not sure what you are asking; perhaps a trick question?

Anyhow, maybe this will assist you in finding enlightenment...
```

#include <iostream>

int main(void)
{
   using namespace std;

   cout << "This is my first line\n"
        << "This is my second line\n"
        << "And this is my very long third line "
           "which I will continue here."
        << endl;

   return 0;
}

```

---

### Post by smdawson on 2010-02-18
That answers my question. I will just use "\n" to keep my words from splitting up from one line of text to the next. Thanks

---

