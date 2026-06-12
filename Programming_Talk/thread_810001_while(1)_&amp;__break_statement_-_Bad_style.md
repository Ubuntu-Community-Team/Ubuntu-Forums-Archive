---
title: "while(1) &amp;  break statement - Bad style?"
date: 2008-05-27
forum: Programming Talk
---

### Post by HunterSBuntu on 2008-05-27
What are your opinions of while(true) loops that are broken out of using a break statement?

Is this considered 'bad' style?

```

while(true)
{
   cout << "Enter temperature followed by unit specifier (23C, 75F):" ;
   cin >> inputString;

   if(validateInput(inputString))
   {      
      break;
   }
   else
   {
      cout << "INPUT FORMAT ERROR - Please try again" << endl;
   }

}
```

I know I could have a do / while sort of like this:

```

do
{
   ....
}while(!validateInput(inputString))

```

The thing is if I do it that way there's no easy way for me to detect invalid input and print the error message on screen in the loop.

I've thought of using a flag type variable to control the loop too but it seems like a waste when I could just use the structure in the first code example.

Do you think there's anything wrong with this sort of use of an infinite loop and a break statement?  Is this something that is generally frowned upon as bad programming style?  To my eye it seems like the clearer and simpler way to do what I want.

---

### Post by pointone on 2008-05-27
Generally, breaking out of loops is considered bad form because it tends to obfuscate your code. It's harder to follow the "flow" of a program with continue/break thrown in everywhere. It's especially worse if you use it in nested loops, etc.

However, in some situations, it's the easiest solution and sometimes the clearest. 

I don't think there's anything wrong with your use. 

However, I personally would use the following in Python (sorry, I don't know C++; I assume you can translate this...):

```
while not validateInput(raw_input("Enter temperature: ")):
    print "Input format error!"
```

...assuming validateInput returns True for "good" input, and False for "bad" input.

---

### Post by ghostdog74 on 2008-05-27
no, definitely not. Use it.

---

### Post by HunterSBuntu on 2008-05-27
That's what I had read too, that it's sort of frowned upon.

Like you said though, I guess it depends on the usage.  If you have all kinds of different conditions with breaks I can see how it can be messy.  Goes against the idea of one entry point, one exit point.

I don't know if there's a way to replicate exactly what you have there in C++ but I get the gist.

The standard console input object I'm using there (cin) doesn't return the inputted string so I can't use the input statement itself as the argument to my validateInput function in the same way.

A funcion call like this wouldn't work

```
validateInput(cin >> inputString); 
```

I guess I could wrap the cin in a function that will return the string that was read but again it seems like I'm making life more complex just to avoid using the break statement.

Food for thought though, thanks for the feedback.

---

### Post by nhandler on 2008-05-27
I personally don't see anything wrong with using the infinite loop and break in your case. You mentioned that you could have used a do-while loop instead of an infinite while loop. However, you were unsure about how to detect invalid input and then output an error message. In order to do that, you simply add an if statement inside the loop. So your code in do-while form would look like this:

```

do
{
   cout << "Enter temperature followed by unit specifier (23C, 75F):" ;
   cin >> inputString;

   if(!validateInput(inputString))
   {      
      cout << "INPUT FORMAT ERROR - Please try again" << endl;
   }
} while(!validateInput(inputString));

```

I personally find that style repetitive, but in the end, it is your code, and your choice.

---

### Post by MikeRaines on 2008-05-27
Hi :)

In my opinion, and the opinion of most of academia that would be considered not best practice.

I just installed Ubuntu so I had to grab the g++ package real quick to test this.

```

#include<iostream>
using namespace std;

int main()
{
        for(bool x=false;!x;)
        {
                int cond=0;
                cout<<"Gimme 5: "<<endl;
                if(cond!=5)
                        cin>>cond;
                if(cond==5)
                {
                        cout<<"Thanks!"<<endl;
                        x=true;
                }
                else
                        cout<<"Thats not 5 Jerk..."<<endl;
        }
}

```

Something along those lines would be considered better practice in my opinion. I'm not sure if this even compiles but I think you get my point :)

Mainly because it lets the reader know that 'x' is the constraint for this loop, rather than some ambiguous break somewhere.

Just in my opinion though :)

---

### Post by kknd on 2008-05-27
I try to evade from this, but I end by using it a lot =).

---

### Post by skeeterbug on 2008-05-28
You can write anything that is unreadable. breaking out of a loop has it's uses (that is why it is there).

---

### Post by dwhitney67 on 2008-05-28
My $0.02 of advice:
[PHP]
#include <iostream>

int main()
{
  int temp = 0;
  char unit;
  bool goodInput = false;

  while ( !goodInput )
  {
    std::cout << "Enter temperature followed by the unit specifier (e.g. 23C, 75F): ";
    std::cin  >> temp >> unit;

    if ( unit != 'C' && unit != 'F' )
    {
      std::cout << "\nBad input!  Try again...\n" << std::endl;
    }
    else
    {
      goodInput = true;
    }
  }

  std::cout << "temp = " << temp << ", unit = " << unit << std::endl;

  return 0;
}[/PHP]

---

### Post by ZylGadis on 2008-05-28
Yes, it is bad style. No, you should not avoid it. The same people who consider it bad style do not like C++ at all, because... they cannot prove theorems about it.
My point is, a good programmer makes code work. A bad programmer makes code look good. Your solution is one of the two optimal ones in this case (the other one involves code repetition). Both are considered bad style. So what?

Edit: dwhitney just proved my point. His piece of code is what is considered good style. If you look at it carefully, you'll see that it introduces an additional variable with the excuse of improved readability in somebody's (not mine) eyes. This is what good style means, and this is what you were intuitively trying to avoid, being inherently a good programmer (intuition about good code is the hallmark of a good programmer: good programmers always have intuition about working code and its optimality, even if they have never heard of big-o notation or spacetime tradeoffs). No offense dwhitney, I know you were trying to help.

---

### Post by dwhitney67 on 2008-05-28
To be a good programmer takes more than merely coding something so that it works.  It also has to be written well enough so that others can understand it, and possibly maintain it in the future.

Many programmers fail to understand this simple concept.  They think they know "everything", but fall miserably short when their work is reviewed by their peers.  Sometimes these programmers are referred to as "hackers", in the good sense of the word, not the bad.


P.S.  Theorems are denoted as such because they have been proven; perhaps you meant to use the word "hypothesis" in your post?

---

### Post by slavik on 2008-05-28
> **MikeRaines said:**
> Hi :)

In my opinion, and the opinion of most of academia that would be considered not best practice.

I just installed Ubuntu so I had to grab the g++ package real quick to test this.

```

#include<iostream>
using namespace std;

int main()
{
        for(bool x=false;!x;)
        {
                int cond=0;
                cout<<"Gimme 5: "<<endl;
                if(cond!=5)
                        cin>>cond;
                if(cond==5)
                {
                        cout<<"Thanks!"<<endl;
                        x=true;
                }
                else
                        cout<<"Thats not 5 Jerk..."<<endl;
        }
}

```

Something along those lines would be considered better practice in my opinion. I'm not sure if this even compiles but I think you get my point :)

Mainly because it lets the reader know that 'x' is the constraint for this loop, rather than some ambiguous break somewhere.

Just in my opinion though :)
I like the code, except that cond will die along with x, and I am assuming that cond needs to live on.

Also, mike, why the assignment statement when declaring cond? it's useless. Also, why the (cond!=5) check? it will always be true (since cond gets set to 0 in the beginning anyway).

---

### Post by ghostdog74 on 2008-05-28
> **dwhitney67 said:**
> My $0.02 of advice:
[PHP]
#include <iostream>

int main()
{
  int temp = 0;
  char unit;
  bool goodInput = false;

  while ( !goodInput )
  {
    std::cout << "Enter temperature followed by the unit specifier (e.g. 23C, 75F): ";
    std::cin  >> temp >> unit;

    if ( unit != 'C' && unit != 'F' )
    {
      std::cout << "\nBad input!  Try again...\n" << std::endl;
    }
    else
    {
      goodInput = true;
    }
  }

  std::cout << "temp = " << temp << ", unit = " << unit << std::endl;

  return 0;
}[/PHP]
looks odd to me. Why is there a need to check for unit != C and unit != F , when "!goodinput" is already understood as "not a good input" ?
```

while(1)
{
  #getinput and check
  if (input is correct ){
   #do stuff
  }else {
   #break or continue. 
  }
}


```

---

### Post by samjh on 2008-05-28
Generally, it is not bad style as long as the logic is obvious, documented, or is self-documenting.

In some languages, loops are designed to be declared in that way.  For example, Ada makes extensive use of arbitrary loops with conditional breaks:
```

   loop
      exit when condition;
   end loop;
```

Problems occur when breaks are positioned or used in ways that are unclear or confusing.

For non-trivial loops, I do what *dwhitney67* demonstrated in his post.

---

### Post by HunterSBuntu on 2008-05-28
The solution dwhitney proposed (using bool flag to control the loop)was the other option I was considering but in this particular case, due to the simplicity of the loop, I thought doing it with the break would not really impact it's readability or make it more confusing.  

And I can save 8 whole bits on a bool. :P

I agree that writing readable, maintainable code is important and I would try to avoid this sort of logic in a complex, core loop with a lot of stff going on in it.  

On the other hand, if you're bending over backwards to make something readable and making your solution more complex than it needs to be seems like you're shooting yourself in the foot.

I guess you gotta strike a balance somewhere in the middle, readable and maintainable without going crazy.

---

### Post by geirha on 2008-05-28
goto-statements are considered very bad practice, yet the linux kernel is packed with them. Linux seems to be working fine for me though, so don't pay so much attention to what's considered good or bad practice, as long as the code does what it's intended to do.

---

### Post by MikeRaines on 2008-05-28
> **slavik said:**
> I like the code, except that cond will die along with x, and I am assuming that cond needs to live on.

Also, mike, why the assignment statement when declaring cond? it's useless. Also, why the (cond!=5) check? it will always be true (since cond gets set to 0 in the beginning anyway).

I just threw it together in a few seconds not thinking and posted it.

```

#include<iostream>
using namespace std;

int main()
{
        int non-local;
        for(int cond=0;cond!=5;)
        {
                cin>>cond;
                if(cond==5)
                {
                        cout<<"Thanks!"<<endl;
                        non-local=cond
                }
                else
                        cout<<"Thats not 5 Jerk..."<<endl;
        }
}

```

This would be my minimal code solution and also addressed the issue of cond's locality. It does however introduce a new variable.

---

### Post by achelis on 2008-05-28
> **ZylGadis said:**
> My point is, a good programmer makes code work. A bad programmer makes code look good.


Sorry but I couldn't disagree more. Making code work does definitely not make someone a good programmer! The good programmer will not only make the code work, but also make sure it's maintainable ie. readable by others. And making code look good (readable by others) does not make you a bad programmer! 

Having multiple exit points however does not necessarily equal bad/unreadable code.

My 0.02€ - extract the code that asks for input to a method that returns the input and replace the break with return input;

---

### Post by [h2o] on 2008-05-28
> **achelis said:**
> Sorry but I couldn't disagree more. Making code work does definitely not make someone a good programmer! The good programmer will not only make the code work, but also make sure it's maintainable ie. readable by others. And making code look good (readable by others) does not make you a bad programmer!

Totally agree. Anyone who has ever taken over a piece of code that "works" and then try to do something with it would know.

I mean come on, sometimes I can't even understand my own code after a few months if it was something I just created in haste.

---

### Post by dwhitney67 on 2008-05-28
> **ghostdog74 said:**
> looks odd to me. Why is there a need to check for unit != C and unit != F , when "!goodinput" is already understood as "not a good input" ?

Can you please read this statement at least 3 times and tell me what is wrong with it?

Why is there a need to check 'unit'???  Well, for one, perhaps some bonehead enters the letter G.  Suppose good input is provided... how do I break out of the loop, short of using a 'break' statement.  Answer, I set the boolean flag to true.

If anything were missing from the conditional statement I provided earlier, it would be a check to verify that the 'temp' value was also sane (i.e. not lower than absolute zero).

Anyhow, rather shoot off you "mouth", why don't you provide an example of your own, that I, as a peer, can evaluate.

---

### Post by dwhitney67 on 2008-05-28
> **MikeRaines said:**
> I just threw it together in a few seconds not thinking and posted it.

```

#include<iostream>
using namespace std;

int main()
{
        int non-local;
        for(int cond=0;cond!=5;)
        {
                cin>>cond;
                if(cond==5)
                {
                        cout<<"Thanks!"<<endl;
                        non-local=cond
                }
                else
                        cout<<"Thats not 5 Jerk..."<<endl;
        }
}

```

This would be my minimal code solution and also addressed the issue of cond's locality. It does however introduce a new variable.

Nice example, but how does this have relevance to what the OP is doing?

Say it did have relevance, would the following not be a cleaner solution?
[PHP]#include<iostream>

int main()
{
  int cond = 0;

  while ( cond != 5 )
  {
    std::cin >> cond;

    std::cout << (cond == 5 ? "Thanks!" : "That not 5; try again...") << std::endl;
  }

  // cond is usable here

  return 0;
}[/PHP]

---

### Post by slavik on 2008-05-28
no, it wouldn't. because using the shorthand for if...else... is not very nice ...

---

### Post by dwhitney67 on 2008-05-28
> **slavik said:**
> no, it wouldn't. because using the shorthand for if...else... is not very nice ...

Well, I am very sorry if I hurt your feelings.  If you got some time to spare, you can read more about the 'ternary' construct here... [http://en.wikipedia.org/wiki/%3F:](http://en.wikipedia.org/wiki/%3F:)

---

### Post by ghostdog74 on 2008-05-28
> **dwhitney67 said:**
> Can you please read this statement at least 3 times and tell me what is wrong with it?

seems like you do not understand what I am saying. I didn't say your code doesn't work. I am saying that when i look at while(!goodinput), i understand you want to evaluate the while loop when the input doesn't satisfy certain condition. Then in this while loop, you started to check the input again , which is unit!=C or unit!=F (false conditions), which is why i find it odd. 

> 
Anyhow, rather shoot off you "mouth", why don't you provide an example of your own, that I, as a peer, can evaluate.

If you have read my post, i have already shown it. i will show to you again

```

 while ( 1 )
  {
    std::cout << "Enter temperature followed by the unit specifier (e.g. 23C, 75F): ";
    std::cin  >> temp >> unit;

    if ( unit == 'C' && unit == 'F' )
    {
  std::cout << "temp = " << temp << ", unit = " << unit << std::endl;
  break; #or return
    }
 
  }


```this is how i would do it (can also use continue instead, but i digress) ....or using your method

```

int main()
{
  int temp = 0;
  char unit;
  bool goodInput = false;

  while ( !goodInput )
  {
    std::cout << "Enter temperature followed by the unit specifier (e.g. 23C, 75F): ";
    std::cin  >> temp >> unit;

    if ( unit == 'C' && unit == 'F' )
    {
      goodInput = true;
    }
    
  }

  std::cout << "temp = " << temp << ", unit = " << unit << std::endl;

  return 0;
}  

```
does it make "sense" to you what I am saying now?

---

### Post by dwhitney67 on 2008-05-28
No, I don't get it.. perhaps I'm slow today.

Your first example is very similar to the one posted by the OP, where he/she questioned whether the use of a 'break' is considered bad programming or not.  IMO, for trivial code, the usage of 'break' is just fine.  The OP's code IMO is trivial.

As for your second chunk of code, is very reminiscent of what I presented, except that you failed to notify the user in the event they provided erroneous data.  With your code, the user would be prompted again for a question that they thought they had just answered!  I think your code could use an else-block.  Perhaps UI design is not your strong suit.

P.S.  I also just noticed that your second chunk of code has a bug.  It is not possible for 'unit' to have the values of 'C' AND 'F' at the same time.  Revisit that if-statement when you get the chance.

---

### Post by raul_ on 2008-05-28
> **ZylGadis said:**
> 
My point is, a good programmer makes code work. A bad programmer makes code look good. 
.
err....:-\" 

moving on...

if you think that's the best of way of doing it, why not add a comment block before you do it so others (probably you, later on, when maintaining the code) understand what the hell is going on. I personally see no other use for comments

---

### Post by dwhitney67 on 2008-05-28
> **raul_ said:**
> err....:-\" 

moving on...

if you think that's the best of way of doing it, why not add a comment block before you do it so others (probably you, later on, when maintaining the code) understand what the hell is going on. I personally see no other use for comments
How long have you been doing s/w development?  In defense of ZylGadis, I've come across lots of code that was documented "well", and yet I was still was unable to understand clearly what is going on.

The worst case scenario, and it happens often, is that some bloke will document the living daylights out of some block of code, and then later change the code without going back to change the documentation.

Best thing IMO is to stay clear of the s/w industry and become a burden on society. *




* You know I'm joking, right?

---

### Post by ghostdog74 on 2008-05-28
> **dwhitney67 said:**
> No, I don't get it.. perhaps I'm slow today.

Your first example is very similar to the one posted by the OP, where he/she questioned whether the use of a 'break' is considered bad programming or not.  IMO, for trivial code, the usage of 'break' is just fine.  The OP's code IMO is trivial.

And i have told OP that its ok to use break

> 
As for your second chunk of code, is very reminiscent of what I presented, except that you failed to notify the user in the event they provided erroneous data.  With your code, the user would be prompted again for a question that they thought they had just answered!  I think your code could use an else-block.  Perhaps UI design is not your strong suit.

P.S.  I also just noticed that your second chunk of code has a bug.  It is not possible for 'unit' to have the values of 'C' AND 'F' at the same time.  Revisit that if-statement when you get the chance.
bugs or no bugs, it can be remedied. I did not put much thought into that.
My main point is the interpretation of the while loop and its conditions.
Your while loop looks like this telling people you want to evaluate the while loop when input is not good.

```

while (not goodinput )
{
  if ( part of input is still not good ) {
    # you have checked input again. Which is unnecessary because you are in the loop already. 
  } 
}

```It is easier to understand when
```

while (not goodinput )
{
  if ( part of input is good ) {
    # do something. break?? or set flag to true
    
  } 
}

```

---

### Post by dwhitney67 on 2008-05-29
I give up... I get better things to do with my life.

---

### Post by samjh on 2008-05-29
> **ghostdog74 said:**
> My main point is the interpretation of the while loop and its conditions.
Your while loop looks like this telling people you want to evaluate the while loop when input is not good.

```

while (not goodinput )
{
  if ( part of input is still not good ) {
    # you have checked input again. Which is unnecessary because you are in the loop already. 
  } 
}

```It is easier to understand when
```

while (not goodinput )
{
  if ( part of input is good ) {
    # do something. break?? or set flag to true
    
  } 
}

```I think whether one is easier to understand than the other, is very subjective and you're not going to settle any disagreements by pushing your own opinion of it.

For me, they're both equally obvious to work out. :)

---

### Post by raul_ on 2008-05-29
> **dwhitney67 said:**
> How long have you been doing s/w development?  In defense of ZylGadis, I've come across lots of code that was documented "well", and yet I was still was unable to understand clearly what is going on.

The worst case scenario, and it happens often, is that some bloke will document the living daylights out of some block of code, and then later change the code without going back to change the documentation.


Then it wasn't well documented. Well documented is not saying what each line of code does.

---

### Post by dwhitney67 on 2008-05-29
Thanks for that insight!  I did not know that.

---

### Post by raul_ on 2008-05-29
Don't get me wrong, I kinda got the point, i just think labeling all programmers that comment their code, as bad programmers is st...well...not accurate

---

### Post by robheus on 2008-05-29
Good loop construct would in this case be:

```

do
  #prompt user for input
  prompt Message
  #get input from user, returning flags:good-input and bail-out
  get_input_from_user(OUT good-input,OUT bail-out)
  #print error message if neither good-input nor bail-out
  if not good-input and not bail-out then
     prompt Error Message
  end if
until good-input or bail-put.

```

---

### Post by NormR2 on 2008-05-29
What about the style of NOT commenting your code. Seems like none of you do it.  Good variable names are better than x and i, but comments can make things clearer.

Whoops, I missed robheus.
BIG WHOOPS!!! I missed pages 2, etc

---

