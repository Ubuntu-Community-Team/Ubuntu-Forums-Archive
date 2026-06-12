---
title: "c++ array[help]"
date: 2006-04-01
forum: Programming Talk
---

### Post by mwanafunzi on 2006-04-01
sup ubuntu,
      I am having some problems with arrays. I want to enter a value into an array of index 5. The first problem i was having was that I was only able to enter one value then the program exits. after g++'ing the file, i get no errors, but when i ./a.out nothing happens (i.e. i get back onto the command line; almost as though i never called the program at all)

any ideas. 

the difference between the first code that I had and this one is that I did not have 
double amount = 0.0;
and I had 
cin >> largest[counter];

Here is my code 

```
#include <iostream>

using namespace std;

int main()
{
	double largest[5], amount = 0.0;
	int counter;

	for(counter = 0; counter < largest[5]; counter++)
	{
		//counter++;
		cout <<"enter value " << counter + 1 << ": ";
		cin >> amount;
		largest[counter] = amount;
		

	}
	
	return 0;
}	
```

---

### Post by FryerFox on 2006-04-01
You need to change:

```
for(counter = 0; counter < largest[5]; counter++)
```

to

```
for(counter = 0; counter < 5; counter++)
```

---

### Post by engla on 2006-04-01
> for(counter = 0; **counter < largest[5]**; counter++)
That comparison is probably not what you want, you want just *counter < 5*

---

### Post by mwanafunzi on 2006-04-01
Thanks guys, tried it and it is working great.

My next quesiont is why would counter < largest[5]  not work?

---

### Post by yaaarrrgg on 2006-04-01
largest[5] is the array's value at index 5.  this isn't even assigned until you are in the loop.  so probably equal to 0.

---

### Post by mwanafunzi on 2006-04-01
cheers

---

### Post by thumper on 2006-04-03
Best to catch these things early...

Unless you are really starting with C (or your professor doesn't know what he's talking about) you really want to be using the std::vector instead of an array.

It is found in the header [<vector>](http://www.cppreference.com/cppvector/index.html).  Definately better to get into the habit of using those.

---

### Post by johnnymac on 2006-04-03
I take a different opinion on this one.....learn the hard way first...then use the easy way.  Lean how the array and such works before looking into vectors...you'll be a more well-rounded developer when your finished and you'll be able to adapt to more languages quickly when you understand the fundamentals of development.

---

