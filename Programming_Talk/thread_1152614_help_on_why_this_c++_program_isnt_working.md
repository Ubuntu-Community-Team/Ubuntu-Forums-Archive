---
title: "help on why this c++ program isnt working"
date: 2009-05-08
forum: Programming Talk
---

### Post by frog4044 on 2009-05-08
i have just begun to program in c++ and i know a little about it so i tried to make a program that factors trinomials except everytime i run it, it gives me floating point exception. can someone tell me why this is happening and why is it doing this?



```
#include <iostream>
using namespace std;

int main()

{

int a, b, c, aa, g;

cout<<"y=ax^2+bx+c\na=";

cin>> a;

cout<<"b=";

cin>> b;

cout<<"c=";

cin>> c;
int i, afi=1;
i=a+1;
int afirstf[10], asecondf[10];
for (i>0; i--;)
{
	if (0==a%i);
	{		
	afirstf[afi]=a/i;
	asecondf[afi]=i;
	afi+=1;
	}
}
int cfirstf[10], csecondf[10];
int z, cfi=1;
z=c+1;
for (z>0; z--;)
{
	if (0==c%z)
	{		
	cfirstf[cfi]=a/z;
	csecondf[cfi]=z;
	cfi+=1;
	}
}
int k=1, ggg;
ggg=cfi+2;
while (k<ggg)
{
	for (int q=0; q<=ggg; q++)
	{
	if (b==afirstf[k]*csecondf[q]+asecondf[k]*cfirstf[q])
	{
	cout<<"("<<afirstf[k]<<"x+"<<asecondf[k]<<")("<<cfirstf[q]<<"x+"<<csecondf[q]<<")";
	}
k++;
}
}
return 0;
}
```

---

### Post by colau on 2009-05-08
Debug your code.
Why
[html]
i=a+1;
for (z>0; z--;)

for (i=a+1;i>0; i--)

and

z=c+1;
for (z>0; z--;)

for (z=c+1;z>0; z--)
[/html]

---

### Post by maheshasolkar on 2009-05-08
This is a 'General Help' forum for Ubuntu related things - At least that is my understanding :) Wouldn't it be more productive to post these kind of questions at, say, stackoverflow.com or some such place?

Having said that, I am sure there are folks in this forum who can help!

---

### Post by MeLight on 2009-05-08
[QUOTE="maheshasolkar"]This is a 'General Help' forum for Ubuntu related things - At least that is my understanding
[/QUOTE]
Bah, and I was sure it says Forum: Programming Talk

[PHP]
for (i>0; i--;)   //initializes at "i>0" ???, and iterates until i-- 
                  //(that is until i == 0, which accidentally matches 
                  //the case you wanted to check)
[/PHP]

My guess is that you don't want to do it (other languages won't even LET you do it :D).
The structure of the for loop is like this:
for(init; condition; update)

what you did was
for(condition**[COLOR="Red"];[/COLOR]** update**[COLOR="Red"];[/COLOR]**)

what you should have done
for(**[COLOR="Red"];[/COLOR]**condition**[COLOR="Red"];[/COLOR]**update)

This sort of works for you anywayz because each time in the condition you lower the i by 1, and finally it reaches 0 (which is also false) and stops the loop

This same thing causes the floating point exception, while the case you WANTED is i > 0, the case you are actully GETTING is i >= 0 (because of of the misplaced condition and update). In the loop you are dividing by i:

[PHP]
for (i>0; i--;)
{
	if (0==a%i);
	{		
	    afirstf[afi]=a/i;//at some point you have a/0 here
	    asecondf[afi]=i;
	    afi+=1;
	}
}
[/PHP]

which is a big no-no when i is zero.

---

### Post by maheshasolkar on 2009-05-08
> **MeLight said:**
> Bah, and I was sure it says Forum: Programming Talk


Well, you are right. It's my bad. I usually answer questions in General Help forum. I wonder how I landed in Programming Talk! My apologies.

---

### Post by frog4044 on 2009-05-08
thanks melight. the placement of the colons was the only thing messing it up. now it atleast solves positive numbers but i am going to fix that later. thanks.

---

