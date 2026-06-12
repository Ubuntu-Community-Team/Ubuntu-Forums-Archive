---
title: "G++ formulas"
date: 2009-05-28
forum: Programming Talk
---

### Post by piasdom on 2009-05-28
hello, how do i get the square of a users input
i want to find the hypotenuse of a triangle. i can square the users' input twice and add them together, but how do i square root THAT answer.if the base is 8 and the height is 6, using my formula (b*h)+(b*h) i get 100 which is incorrect.the answer is 10. how do i get the square root ((b*h)+(b*h)) ?
thanks


p.s. 
in using G++ in ubuntu hardy(8.04).
this is for a simple(i hope) calculator.

---

### Post by kjohansen on 2009-05-28
Not to be rude, but you could have easily searched for your answer...

[php]

#include <cmath>


....
float myvar=some value;

float sqrt_of_my_var=sqrt(myvar);


...

[/php]

---

### Post by piasdom on 2009-05-28
you're not rude.and thanks for answering. but i've been searching for two weeks for this one formula. i'm new to G++ and these forums.again..thanks a lot

---

### Post by monkeyking on 2009-05-28
Hi

look at this for other map related stuff
[http://www.cplusplus.com/reference/clibrary/cmath/](http://www.cplusplus.com/reference/clibrary/cmath/)

[PHP]
#include <iostream>
#include <cmath>

int main(){
  int in = 10;

  std::cout <<"sqrt of: "<<in <<" = " <<sqrt(in) <<std::endl;

}
[/PHP]

---

### Post by nvteighen on 2009-05-29
Er... the language is called **C++** :) g++ is just a compiler among others. Maybe that's why you didn't find anything.

---

### Post by matthew.ball on 2009-05-29
A square root is a number raised to a half power.

9^0.5 = 3 etc.

---

### Post by lisati on 2009-05-29
> **piasdom said:**
> hello, how do i get the square of a users input
i want to find the hypotenuse of a triangle. i can square the users' input twice and add them together, but how do i square root THAT answer.if the base is 8 and the height is 6, using my formula (b*h)+(b*h) i get 100 which is incorrect.the answer is 10. how do i get the square root ((b*h)+(b*h)) ?
thanks


p.s. 
in using G++ in ubuntu hardy(8.04).
this is for a simple(i hope) calculator.

Um, is it a right angled triangle? If so, isn't the it more like a^2=b^2+c^2??????

---

### Post by piasdom on 2009-05-29
> **lisati said:**
> Um, is it a right angled triangle? If so, isn't the it more like a^2=b^2+c^2??????
thank ya'll for answering,
guess i need to show my progress:

			
			cout << "enter base: ";
			cin >> user_input;
			cout << "enter height.";
                        cin >> user_input2;
			cout << "the hypotenuse is " << ((user_input*user_input)+(user_input2*user_input2)) << endl;

  the end is where i'm stuck.how do i get the sqrt of the last cout? and i can't figure out how to use what you showed me kjohansen and monkeyking.

i know this is not the answer forum,it's a discussion forum.and as soon as someone new comes here, they realise they need to do the work.i'm trying to learn this as to get a better position at work.to ALL who answered.  THANKS .. greatly appreciated

---

### Post by monkeyking on 2009-05-29
you can do something like

[PHP]

cout << "enter base: ";
cin >> user_input;
cout << "enter height.";
cin >> user_input2;
cout << "the hypotenuse is " << sqrt((user_input*user_input)+(user_input2*user_input2) ) << endl;
[/PHP]

or a more intuitive way


[PHP]
float a,b,c;
cout << "enter base: ";
cin >> a;
cout << "enter height.";
cin >> a;

c=sqrt(a*a+b*b);

cout << "the hypotenuse is " << c << endl;
[/PHP]

---

### Post by piasdom on 2009-05-29
> **monkeyking said:**
> you can do something like

[PHP]

cout << "enter base: ";
cin >> user_input;
cout << "enter height.";
cin >> user_input2;
cout << "the hypotenuse is " << sqrt((user_input*user_input)+(user_input2*user_input2) ) << endl;
[/PHP]

or a more intuitive way


[PHP]
float a,b,c;
cout << "enter base: ";
cin >> a;
cout << "enter height.";
cin >> a;

c=sqrt(a*a+b*b);

cout << "the hypotenuse is " << c << endl;
[/PHP]
thanks monkeyking, that worked great. Peace to all

---

