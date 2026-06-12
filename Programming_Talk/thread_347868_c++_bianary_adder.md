---
title: "c++ bianary adder"
date: 2007-01-27
forum: Programming Talk
---

### Post by ewtesterman@cox.net on 2007-01-27
I have been working on this code for a school assignment, I am to create a binary adder in c++. My code compiles and runs. The carry is updating correctly however my sum does not and I am not sure why. Any help would be great.

```

#include <iostream>
#include <iomanip>
#include <bitset>


using namespace std;

void print_bool (bitset<4> bs)
{
     for ( int i = (int) bs.size()-1; i >= 0; i--)
                  {cout << bs[i] ;}
          cout<<endl;
}

int main()
{
          int int_a=0, int_b=0, final= 0; 
          
     cout <<"Eneter two intager values: "<<endl;
     cin >>int_a>>int_b;

     bitset<4> bool_a (int_a);
     bitset<4> bool_b (int_b);
     bitset<4> sum, carry = 0;

     cout <<endl;
     cout<<endl;

     sum = bool_a ^ bool_b;
     carry = bool_a & bool_b;
     carry = carry <<1;
    
     for (int i  = 0; i < 3; i++)
         {
                   print_bool(carry);
           print_bool(bool_a);
           print_bool(bool_b);

                   carry[i+1] = bool_a[i] & bool_b[i] | carry[i] & (bool_a[i] ^bool_b[i]);//would like to get rid of the the + in carry[i+1]
           sum[i] = bool_a[i] ^ bool_b[i];
           sum = sum[i] ^ carry[i];

           cout <<"----"<<endl;
           print_bool(sum);
               cout<<endl;
               cout<<endl;
           final = sum.to_ulong();
               cout<<int_a<<" + "<<int_b<<"  = "<<final<<endl;
     }
}

```

---

### Post by ewtesterman@cox.net on 2007-01-28
Its always bet when you solve your own problems. I had trouble finding any kind of real example on this so here it is for anyone else.

```

// Comp Org Mon and Wed
// Assignment I    Due Jan 31 2007
// Eric W. Testerman   ewtesterman@gmail.com
//
//
//This Program will take in two integer values seperated by a space.
//It will then use logical bit operators ( & | ^ ) to add binary numbers
// the problem and solution will be writen to the screen in both dec and binary.
#include <iostream>
#include <iomanip>
#include <bitset>


using namespace std;

void print_bool (bitset<8> bs)    //This function runs through the bitsets passed to it writing them to the screen
{                                                     //with an endl at the end it.
    for ( int i = (int) bs.size()-1; i >= 0; i--)
        {cout << bs[i] ;}
        cout<<endl;
}

int main()
{
//****************************Declare variables and initialize data values includes taking inputs**************************
    int int_a=0, int_b=0, final= 0; 
    
    cout <<"Eneter two positive intager values seperated by a space"<<endl;    //Askes for the input and takes in the input as intagers
    cout<<endl;                                
    cin >>int_a>>int_b;
    
    bitset<8> bool_a (int_a);    //These bitset statemens creates the binary values I will work with two to represnt the integers to be added
    bitset<8> bool_b (int_b);    //as well as a sum and carry all intialized to 0
    bitset<8> sum, carry = 0;
    
    cout <<endl;
    cout<<endl;
    //******************************************Computations are performed here*****************************************
    sum = bool_a ^ bool_b;        //Gets the starting sum by using exclusive or s = a xor b
    carry = bool_a & bool_b;    //The starting carry is c = a and b
    carry = carry <<1;        //YOU HAVE TO SHIFT THE BITS IN THE CARRY TO MAKE THEM LINE UP
                    //THIS INSURES THAT THE FIRST ONE ON THE RIGHT IS ALWAYS A ZERO
                    //This is also know as a half adder    
    
    for (int i  = 0; i < 7; i++)    //Sets up the loop to iterate through the bits for the full adder
    {
        carry[i+1] = bool_a[i] & bool_b[i] | carry[i] & (bool_a[i] ^bool_b[i]);    //  c = x and y or z and (x xor y)
        sum[i] = (bool_a[i] ^ bool_b[i]) ^ carry[i];                // s = (x xor y) xor z
    }    

//The key there is that z needs to be your c from the previous itteration
//hence having to establish starting values the full adder must be feed by
//an half adder    
//*************************************Printing and formating**************************************
    cout<<"c ";                                                    
    print_bool(carry);
    cout<<"  ^^^^^^^^"<<endl;
    cout<<"  ";
    print_bool(bool_a);
    cout<<"+ ";
    print_bool(bool_b);
    cout <<"----------"<<endl;
    cout<<"  ";
    print_bool(sum);
    cout<<endl;
    cout<<endl;
    final = sum.to_ulong();    //This converts the bitset back to an interger value to printed to the screen
    cout<<int_a<<" + "<<int_b<<"  = "<<final<<endl;
}


```

---

### Post by Wybiral on 2007-01-28
I'm not sure how you did it... (sorry, the code in un-indented and I'm in the middle of another project, btw... using the [ c o d e ] tag on the forums lets you enter formated code in)

But I would probably do a binary adder by using a decrementer and an incrementer.

Decrement the right operand until it is 0, and increment the left operand every time you decrement the right.

Binary dec/inc functions are very simple...

Inc: Start at the right. If you hit a 1, change it to a 0 and stop... Otherwise keep going until you find a 0 (which you change to a 1). Move left each loop.

Dec is the exact opposite of inc... It's very simple this way. I'm not sure how you did it, but if it works, great!

Naturally, it would be easier to convert the bitset to an integer, add them, then convert them back to bitsets... But that's probably not allowed is it?

Good luck!

---

### Post by jblebrun on 2007-01-28
> **Wybiral said:**
> I'm not sure how you did it... (sorry, the code in un-indented and I'm in the middle of another project, btw... using the [ c o d e ] tag on the forums lets you enter formated code in)

But I would probably do a binary adder by using a decrementer and an incrementer.

Decrement the right operand until it is 0, and increment the left operand every time you decrement the right.

Binary dec/inc functions are very simple...

Inc: Start at the right. If you hit a 1, change it to a 0 and stop... Otherwise keep going until you find a 0 (which you change to a 1). Move left each loop.

Dec is the exact opposite of inc... It's very simple this way. I'm not sure how you did it, but if it works, great!

Naturally, it would be easier to convert the bitset to an integer, add them, then convert them back to bitsets... But that's probably not allowed is it?

Good luck!

Looking at his description of the assignment, and his terminology in comments (like 'full adder') it looks like he's supposed to mimic binary adder hardware. What class is this for, ewtesterman?

In any case, your choice of algorithm seems odd to me... when would it make sense to add numbers using an algorithm like that?

---

### Post by Wybiral on 2007-01-28
You're right, that's obviously the worst solution you could use in C++
I just use that alot in my turing machine programs.
An obviously more efficient method would be to use a carry flag and iterate once from right to left.

My first post if only logical when you can't use variables... So C++ is obviously a bad time to use it.

I was just in the middle of something and thought I had at least an alternate solution to however he did it, but yes... Bad idea. (though it does work like a charm when you can't use variables, such as with a turing machine)

---

### Post by ewtesterman@cox.net on 2007-01-28
Well this was for a class called Computer Organization, the class is about how the boolean logic can represent hardware solutions, I understand that we will start to use assembly soon this assignment was to do it in whatever language you already know, (in my case know of). I appreciate the feedback and am very open to critiques of my code. That is how we learn right. Anyway. As far as the algorithm well that is what my book "Logic and Computer Design Fundamentals" had. The book only gives them in mathematical terms and diagrams, so maybe there is a better way to do it in c++. The assignment just states to use the boolean logic to perform the calculations. So the feedback is welcome. Thanks all.

---

### Post by jblebrun on 2007-01-28
> **ewtesterman@cox.net said:**
> Well this was for a class called Computer Organization, the class is about how the boolean logic can represent hardware solutions, I understand that we will start to use assembly soon this assignment was to do it in whatever language you already know, (in my case know of). I appreciate the feedback and am very open to critiques of my code. That is how we learn right. Anyway. As far as the algorithm well that is what my book "Logic and Computer Design Fundamentals" had. The book only gives them in mathematical terms and diagrams, so maybe there is a better way to do it in c++. The assignment just states to use the boolean logic to perform the calculations. So the feedback is welcome. Thanks all.


Have you ever taken a digital logic class? You might be interested in reading up on digital logic design, and how binary adders are created. (At the very least, you should understand what a half-adder and full-adder are, and how they work to add two single bits).

There is, of course, a better way to add two binary numbers in C++. But if you're trying to emulate the behavior of hardware, then you are constrained in what you can do. Not everything that you can do in C++ can be trivially represented using hardware. So, this is a nice exercise for you, because it will give you an introduction to the way things work. 

For example, Wybiral's example wouldn't make much sense in hardware, because it is self-referential. His algorithm uses an increment and decrement operation, but to increment in hardware you need an adder. So you see the problem. 

The most basic binary adder based on a full adder is a **ripple adder**. This is also a slow solution, because you have to calculate the bits 1 at a time. You add the first bits, get the carry, add the second two bits with the carry, and so on. There are adders for larger numbers that are much more efficient. For example, you can compute "carry lookahead" values that calculate the carry values for the higher bits without waiting for the carry to "ripple" up from the least significant bit. If you really want to explore more (and maybe impress your teacher), try implementing a carry lookahead adder!

I'm happy to give you some suggestions with your implementation, but it's not clear to me what sort of advice you're looking for. You've posted two code examples: are they both written by you, or is one an example from somewhere else?

---

### Post by Lux Perpetua on 2007-01-28
> **jblebrun said:**
> The most basic binary adder based on a full adder is a **ripple adder**. This is also a slow solution, because you have to calculate the bits 1 at a time. You add the first bits, get the carry, add the second two bits with the carry, and so on. There are adders for larger numbers that are much more efficient. For example, you can compute "carry lookahead" values that calculate the carry values for the higher bits without waiting for the carry to "ripple" up from the least significant bit. If you really want to explore more (and maybe impress your teacher), try implementing a carry lookahead adder!It kind of destroys the performance advantage if it's not implemented in hardware or on parallel processors. ;-)

---

### Post by ewtesterman@cox.net on 2007-01-28
> **jblebrun said:**
> I'm happy to give you some suggestions with your implementation, but it's not clear to me what sort of advice you're looking for. You've posted two code examples: are they both written by you, or is one an example from somewhere else?

The class I am taking is supposed to be a combination of digital logic and assembly (Was just assemble until this semester).  I am struggling because the book did not come in until a week ago. Both code examples are mine sorry for the confusion. The original assignment can be seen [here]("http://www.comsc.ucok.edu/%7Estockwel/co1.html"), however, that is the assignment from when this was only an assembly class, so we were told that the binary adder is what he wants. I would love to do the assignment as written. I guess I just wanted to post because I have not been very successful in finding much out there (at a novice level) with live discussion on these topics. I really like to learn from communities then I get to see more perspectives. Thanks for all the feed back.

You were correct in your assumptions that the focus of the assignment is just to better understand the digital logic. 

I keep seeing people talk about the efficiency I would like to know what you mean. Is it not efficient to to use an a full binary adder or is is not efficient to use my binary adder above. I am sure my code could use some work. It always can.

---

### Post by jblebrun on 2007-01-28
> **Lux Perpetua said:**
> It kind of destroys the performance advantage if it's not implemented in hardware or on parallel processors. ;-)

Yes, but if the goal was actual performance advantage, he wouldn't be writing this complicated C++ code at all. He's just write a+b. The point here is to gain some insight into the way hardware  works.

---

### Post by jblebrun on 2007-01-28
> **ewtesterman@cox.net said:**
> 
I keep seeing people talk about the efficiency I would like to know what you mean. Is it not efficient to to use an a full binary adder or is is not efficient to use my binary adder above. I am sure my code could use some work. It always can.

Well, efficiency means different things in hardware and software. When you're designing hardware, you have to thing about the time that it takes for an electrical signal to travel through a number of transistors. When you program, you think at a much higher level (even if you're programming in assembly!), about how many cycles a CPU will take to execute something. 

When you design a binary "ripple adder", you actually chain a number of full adders together. The adder that adds the second two bits won't show the right answer until the adder for the first two bits has settled on an answer, the adder for the third two bits won't show the right answer until the adder for the second two is done, and so on. So, for example, if it takes 1 microsecond for the signals to travel through one full adder, it will take 32 microseconds until the ripple adder displays the correct answer. 

Hardware design researchers investigate ways to decrease this delay. One example of this is a "carry-lookahead" adder. What happens here is that special logic is designed that can quickly figure out just what the carry value will be, for some number of bits. For example: imagine that you create a circuit that looks the first 16 bits of the number, and decides what the carry from bit 16 to17 will be. Now, imagine that this carry lookahead circuits takes 2 microseconds to settle on that answer. Now you've reduced the time to do the addition to 18 microseconds, because you can start adding the second half of the number in 2 microseconds, rather then waiting 16 microseconds for the cary value to propagate that far. 

Does this make sense?

Anyway, this might be going a bit too far for an introductory assignment! So maybe just sticking with what you're doing is fine!

---

### Post by jblebrun on 2007-01-28
Wikipedia has a really good article explaining how binary adders work, and giving a better explanation of ripple-carry adders and carry-lookahead addres.

[http://en.wikipedia.org/wiki/Adder_(electronics](http://en.wikipedia.org/wiki/Adder_(electronics))

Use the block diagrams to guide the design of your code. 

By the way, can you go edit your other posts and put your code in ```
 
``` tags so that it is formatted nicely?

---

### Post by ewtesterman@cox.net on 2007-01-28
Thanks for the link it looks like some good reading. Your link is missing the last ) so it does not work, but that is an easy fix. I will not be able to do it tonight, but tomorrow I would like to at least add the ability to do the subtraction, multiplication, and division. These look like the can be done by bit shifting, much easier. If you would elaborate on the registry and accumulator parts (from the original assignment) that would be cool. I know that since my professor says he is not a hardware guy that he is just going to focus on the Assembly stuff, but after I spent 6 years in Industrial automation with PLC's and Relay and Ladder Logic, this all seems to be really cool and a lot of it so far is stuff I wanted to know. I found the parts in the book about Gray scale to be very cool. Sometimes I want to change my major to EE, but I have gone to far to change now. 

Also I am curious I don't know where to start on this but I would like to make my programs have a gui, but like aptitude or mc from the command line. What are the tool kits for that, preferable something cross platform. I do my best to try and study portable code.

---

### Post by jblebrun on 2007-01-28
> **ewtesterman@cox.net said:**
> Thanks for the link it looks like some good reading. Your link is missing the last ) so it does not work, but that is an easy fix. I will not be able to do it tonight, but tomorrow I would like to at least add the ability to do the subtraction, multiplication, and division. These look like the can be done by bit shifting, much easier. If you would elaborate on the registry and accumulator parts (from the original assignment) that would be cool. I know that since my professor says he is not a hardware guy that he is just going to focus on the Assembly stuff, but after I spent 6 years in Industrial automation with PLC's and Relay and Ladder Logic, this all seems to be really cool and a lot of it so far is stuff I wanted to know. I found the parts in the book about Gray scale to be very cool. Sometimes I want to change my major to EE, but I have gone to far to change now. 

Also I am curious I don't know where to start on this but I would like to make my programs have a gui, but like aptitude or mc from the command line. What are the tool kits for that, preferable something cross platform. I do my best to try and study portable code.

What sort of GUI do you want for this program? If you want a console-based GUI, your best bet is explore the curses/ncurses library. But I would make that the *last* thing you investigate: your teacher will certainly appreciate a nice GUI, but not if the basic functionality of the program is not there!

The assignment is cool. What are you are doing is building a virtual machine (just like Java!). This is the first step to learning how to write a emulator (like a Commodore 64 emulator or a Nintendo emulator). This is a very basic virtual machine, of course.  However, he doesn't give you any specifications about an instruction set architecture, so I guess you'll need to make your own. Assuming you're familiar with assembly, you should be able to come up with the instructions that you need for this simple computer. Then, you need to write something that can read in a serious of machine instructions and execute them!

I'm being purposely vague here, because I don't want to do your homework for you! I can help you more if you ask very specific questions.

---

### Post by ewtesterman@cox.net on 2007-01-31
As far as the gui issue it is certainly not for this program, however I am in another programming class and we are still doing console based stuff in c++. I really like being able to be a little more creative with the UI.

As for the assignment I need to clarify. The assignment you saw was from when the class was just assembly. All I had to do was make the adder, since we have not learned any assembly at all. So I guess they were just lazy, instead of rewritting the assignment, and told us just to do the adder in c++

---

