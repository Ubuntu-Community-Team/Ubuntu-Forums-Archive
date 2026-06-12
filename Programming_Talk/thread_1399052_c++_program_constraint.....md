---
title: "c++ program constraint...."
date: 2010-02-05
forum: Programming Talk
---

### Post by abhilashm86 on 2010-02-05
i was solving[ uva problem]("http://uva.onlinejudge.org/index.php?option=com_onlinejudge&Itemid=8&category=3&page=show_problem&problem=36"), i get output but minor details i'm not understanding, what is less in following code? 

this is problem,

Time limit: 3.000 seconds 
Sample Input

1 10
100 200
201 210
900 1000

Sample Output

1 10 20
100 200 125
201 210 89
900 1000 174

```
#include<iostream>
using namespace std;

unsigned int cycle(int a, int count )
{
	
	if(a == 1) return count;
	
	if((a%2) == 0)
			return cycle(a/2,++count);		
	else
		return cycle((3*a)+1, ++count);
	
}



unsigned int maxcycle(int i, int j )
{
	unsigned int count = 0;
	
	for(int k=i; k<=j; k++)
	{
	 	unsigned int temp;
			if(i>j) swap(i, j);		
		
		temp = cycle(k, 1);
		if(temp > count) 
		count = temp;
			
	}
	return count;
}


int main()
{
	unsigned int i ,j;
	while(cin>>i>>j)
	{
		cout<< i << " " << j <<" " <<maxcycle(i, j) <<endl;
	}

}


```
the uva judge don't tell whats exactly wrong? so i don't know what i need to change? 
is there any better place/website for coding practice, where i get to know more things where i'm going wrong and easier?

---

### Post by dribeas on 2010-02-05
What does the response message actually say. IIRC there are a fix set of reasons for the problem to be rejected, runtime errors, timeouts, invalid result, incorrect formatting...

---

### Post by LKjell on 2010-02-05
I suggest then you try to learn java and do stuff which is not so scientific related.

Reason for java is that if you type an error it will print out the line you need to edit.

Math related problems can be fun when you are able to solve them. But some students just hit their head hard when they are presented to do some heavy algorithm and data structure.

---

### Post by MadCow108 on 2010-02-05
> **LKjell said:**
> I suggest then you try to learn java and do stuff which is not so scientific related.

Reason for java is that if you type an error it will print out the line you need to edit.

c++ (and almost every other language) does the same...

edit: probably found the problem:
you code fails on swapped input
10 1
outputs 
10 1 0

your method of ordering the input for your loop is wrong

---

### Post by abhilashm86 on 2010-02-06
> **MadCow108 said:**
> c++ (and almost every other language) does the same...

edit: probably found the problem:
you code fails on swapped input
10 1
outputs 
10 1 0

your method of ordering the input for your loop is wrong

thats good, i shifted swap condition above, now its working good. Thanks:D

---

### Post by abhilashm86 on 2010-02-06
> **LKjell said:**
> I suggest then you try to learn java and do stuff which is not so scientific related.

Reason for java is that if you type an error it will print out the line you need to edit.

Math related problems can be fun when you are able to solve them. But some students just hit their head hard when they are presented to do some heavy algorithm and data structure.

yes while solving strong algo and recursions, my head goes blank, i've heard many classes are built in java!! easy to do, but i like c++, want to learn more by doing loads mistakes!!

---

