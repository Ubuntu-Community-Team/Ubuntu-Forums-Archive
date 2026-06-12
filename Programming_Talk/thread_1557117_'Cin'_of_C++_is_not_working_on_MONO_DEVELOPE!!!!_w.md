---
title: "'Cin' of C++ is not working on MONO DEVELOPE!!!! what can i do??? plzz help  :'("
date: 2010-08-20
forum: Programming Talk
---

### Post by shock_the_rock on 2010-08-20
hello there everyone! I am a brand new user in ubuntu and trying to programming c++ in ubuntu, so I have installed IDE like Mono develope, In mono develope it comiles the program easily but dont take any input that is console input. It doesn't manage to work the 'cin' command. As an example: 

#include<iostream>
using namespace std;

int main()
{
    int i;
    std::cout<<"This is output.\n";
    
    //input number using>>
    cout<< "Enter a number:";
    
    cin>>i;
    
  //now output a number using << 
    
    cout << i <<"\nsquared is:"<<i*i<<"\n";
    
    return 0;
}

in the above code all works it show output but  with garbage numbers as it did not take any input. 

the output is as like as : 

This is output.
Enter a number:-1074021896
squared is:1130913856


Now what can i do?  :( plz help me. I also have the NET BEANS IDE but i cant managed to work in it. Please suggest me plz plz

---

### Post by john newbuntu on 2010-08-20
In situations like these, you can not trust the user to enter a number.  You have to, in your program make sure that the number entered is a valid integer or in this case, check if the 'cin' stream is in a good state after reading the value to i.  
I'll let you figure out the solution as it is an interesting one for a beginner and a good way to learn C++.

---

### Post by Vaphell on 2010-08-20
what did you enter when you got the garbage?

---

### Post by shock_the_rock on 2010-08-20
is it demands data encapsulation? or anything like this? plz gimme some hint.

---

### Post by shock_the_rock on 2010-08-20
it never asks for any input how can i give input to it that is the question, it never asks for the value of i, it directly shows the output with those kind of i's value. Is it a bug or my fault i cant understand.

---

### Post by Vaphell on 2010-08-20
your code works perfectly when compiled manually with g++, i have no idea why it fails here :/
ide has to create executable file somewhere, does it fail too, when run from terminal?

---

### Post by cariboo on 2010-08-20
Moved to Programming Talk.

---

### Post by Paul820 on 2010-08-20
There isn't anything wrong with your code. If you are having trouble with your ide, why don't you either use gedit and compile from the command line, or use geany which is an excellent little program. Or, get codeblocks, another excellent program. Geany and codeblocks are in the repositories.

---

### Post by shock_the_rock on 2010-08-20
yup when i compile from gedit it works perfectly, but in mono develope ide it doesn't, may be it's a bug or any feature that i can't use at this primary stage, i want a environment in where i can code c++ and compile, run, edit, explore,debug and ofcourse learn it well and it works correctly as i am new in this linux world i am feeling insecure where can i find it and how so please give me some suggestions and paths how i can grab it well and i feel very much interest in ubuntu that i want to discard windows like germ from my life so i have to familiar and have sufficient tool to enjoy it.... I wanna your help as i have known you'll help me :) thanks to all buddies. :) additionally i want to say that i installed another three ide, ECLIPS (only JAVA works) NET BEANS i failed to work in it , ANJUTA( I tried to programming c++ from last night but cant compile any file yet :( ) I NEED A PERFECT C++ ENVIRONMENT WHERE I CAN RUN SMOOTHLY WITH CODING...

---

### Post by shock_the_rock on 2010-08-20
> **cariboo907 said:**
> Moved to Programming Talk.

thanks for your move :)

---

### Post by Paul820 on 2010-08-20
Get yourself codeblocks from synaptic. Or open a terminal and
> sudo apt-get install codeblocks
It is a really easy IDE to start using if you need one. You can write, compile, debug (breakpoints) all in the same program.

---

### Post by shock_the_rock on 2010-08-20
> **Paul820 said:**
> There isn't anything wrong with your code. If you are having trouble with your ide, why don't you either use gedit and compile from the command line, or use geany which is an excellent little program. Or, get codeblocks, another excellent program. Geany and codeblocks are in the repositories.


thanks paul!!!! thanx thanx thanx!!! :D i have found what i wanted!!! thanx a lot for your help, i have installed geany and its so fine! 

Can i ask another additional question, How can i use oracle in ubuntu? i want to install it, how can i do it? i am beginner in oracle.

---

### Post by Paul820 on 2010-08-20
Oracle? Don't know what you mean, maybe someone else can help you with that.

---

### Post by shock_the_rock on 2010-08-20
thank u again for ur help :)

---

