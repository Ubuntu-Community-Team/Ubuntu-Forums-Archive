---
title: "Simple question about functions in C++."
date: 2011-02-01
forum: Programming Talk
---

### Post by Jordii on 2011-02-01
I just created this code:
```
#include<iostream>

void count(int);
int num;
using namespace std;


int main()
{
cout << "Enter a number: ";
cin >> num;
while(num < 100000)
{count(num);}


cin.get();
return 0;    
}



void count(int number)
{
    cout << num << endl;
    num = num+1;
}

```As you can see, it asks the user to enter a number and keeps adding one to it until the result of num+1 is higher than 9999. I've created another program just like this, but without the function. In the code above the function needs the variable "num" to exist in the program, but now, I want to use the same function (count) in another program where I for example use "x" in stead of "num". I can't seem to get the function working by just entering "num" or "x" as the argument of the function. I changed the code in the following:
```
#include<iostream>

void count(int);
int num;
using namespace std;


int main()
{
cout << "Enter a number: ";
cin >> num;
while(num < 100000)
{count(num);}


cin.get();
return 0;    
}



void count(int number)
{
    cout << number << endl;
    number = number+1;
}
```This doesn't give the result I expected. All the program does is it keeps repeating the number that the user enters. 

I expect the problem to be the very last line of the function count, "number = number + 1;". If I change this line into  "num = number + 1;", the program seems to work just fine. 
Does anyone know what I did wrong?  How can I change the function so that I can use it without having to use variables that I created outside of the function (and having to change the function every time).

Thank you very much for reading!

---

### Post by slooksterpsv on 2011-02-01
The joy of pointers! =D

I don't know how to explain it, cause I barely know how I work, but this is a working example of what you're trying to do.

```

#include <iostream>

using namespace std;

int x = 0;

void count(int* num)
{
 cout << *num << endl;
 *num += 1;
}

int main()
{
	cout << x << endl;
	while(x < 100)
		count(&x);
	return 0;
}

```

Now I'm going to see if I can explain this, when you pass &x to count you're passing the address of the variable x, which is taken over by num, to access the data/value of x, you have to use the unary operator * to access the address of the variables data.

Another common name is an indirection variable - [http://en.wikipedia.org/wiki/Indirection](http://en.wikipedia.org/wiki/Indirection)

Hope that helps and hope this is not homework.

---

### Post by worksofcraft on 2011-02-01
> **Jordii said:**
> 
....
[php]
void count(int number)
{
    cout << number << endl;
    number = number+1;
}[/php]

This doesn't give the result I expected. All the program does is it keeps repeating the number that the user enters. 

I expect the problem to be the very last line of the function count, "number = number + 1;". If I change this line into  "num = number + 1;", the program seems to work just fine. 
Does anyone know what I did wrong?  How can I change the function so that I can use it without having to use variables that I created outside of the function (and having to change the function every time).

Thank you very much for reading!

C++ is a great language for learning concepts because it supports such a wide variety of them ;)

In this case parameter passing.

Your count method is passing the parameter "number" by value, so what that does is to create a local copy of the number's value for the function to use internally.

When you increment it, all that happens is you add one to that local copy and not to the original.

If you want to affect the original then you must pass it by reference. In C++ you can do this with the & symbol like so:

[php]
void count(int & number)
{
    cout << number << endl;
    number = number+1;
}
[/php]

The reason it works with "num" instead of "number" is because you have declared num to be a global variable. That means it is accessible to everything without needing to pass it anywhere. Global parameters are considered a bad idea because it is hard to work out what may or may not affect them in large programs.

I hope that helps :)

p.s. you will also have to chage the function prototype like so:
[php]
void count(int &);
[/php]

Note: Personally I prefer to write my programs back to front with main at the bottom after everything else has been defined... it doesn't mean you have to do "bottom up" programming it just means that you insert the lower levels before the higher ones that use them... and then you start reading at the bottom and bubble your way up to the top ;) Incidentlay I wrote something about the [natural direction of writing]("http://code.google.com/p/speaknumber/downloads/list") R2L.3.html in that project if you are interested ;)

---

### Post by nvteighen on 2011-02-02
Why are we discussing pointers!?

No, this is better done by using a return value. Yes, the solutions given so far work and in some occasions they are the way to go because it uses less memory, but not in the case where memory isn't of concern.

Return values are the functions' "result". For example:

```

int sum(int a, int b)
{
    return a + b;
}

```

That's a function that takes two integers and returns an integer (the return type is the one before the function's name). You specify the function's return value using the return statement. Returning will, obviously, interrupt the function's execution and pass the result to the function's caller.

So, for example:
```

#include <iostream>

int max(int x, int y)
{
    /* There are better ways to write this. Going for clarity here. */

    int result = x;
    if(result < y)
        result = y;

    return result;
}

int main(void)
{
    int biggest = max(2, 9); // biggest will be 9, of course.
    std::cout << "biggest = " << biggest << std::endl;

    int input;
    std::cin >> input;

    int another_biggest = max(input, biggest); // Reusing max :)
    std::cout << "another_biggest = " << another_biggest << std::endl;

    return 0; // <- Oh, and what's this?
}

```

Do you see what's happening there? As max returns an integer, I'm able to take that result and store it in a variable. This way, you can "feed" the function with any value and get a result from it without any hassle. If you want, you can reassign the original variable with the result you gave it...

Moreover, did you ever wonder why main() uses that "return 0;" line? Well, because you can use main's returnvalue to tell the OS whether the program exited succesfully or not (in most OSs, 0 means "ok" and everything else means some error).

The pointer solution, instead, reuses the **memory address** of the argument you gave. Please, don't get me wrong: it's also a good solution and sometimes it's the only solution, but you have to understand that by doing that you're overwriting the original variable. My solution is more flexible in that respect: you can overwrite the original variable or not... The cost, of course, is that you have to use a little more memory to hold the return value.

On something else: IMO, your count function should have the loop inside of it... You're somehow splitting the same "task" in two places... It's not bad, but it looks a bit weird to my eyes.

---

### Post by Jordii on 2011-02-02
Thank you both! That should get me further. It´s no homework, by the way. I`m trying to learn a bit of programming as a self-tuition. I will definitely take a look at that article in your reply when I´ve got some more free time, worksofcraft! :smile:
 
@nvteighen, I hadn´t seen your reply before I posted this, so I´ll reply to it right now. I understand your example but I´m not sure how I should use the return function in my little program. 
I know I could´ve put the whole loop inside of the count function, but I just wanted to mess around with it a bit. Thank you!

---

### Post by slooksterpsv on 2011-02-02
> **Jordii said:**
> Thank you both! That should get me further. It´s no homework, by the way. I`m trying to learn a bit of programming as a self-tuition. I will definitely take a look at that article in your reply when I´ve got some more free time, worksofcraft! :smile:
 
@nvteighen, I hadn´t seen your reply before I posted this, so I´ll reply to it right now. I understand your example but I´m not sure how I should use the return function in my little program. 
I know I could´ve put the whole loop inside of the count function, but I just wanted to mess around with it a bit. Thank you!

You could do this:
```


int count(int x)
{
 cout << x << endl;
 return x;
}

int main()
{
 int y = 0;
while (y <= 100)
 y = count(y+1);
}

```

That would work I believe.

---

### Post by Jordii on 2011-02-02
Yes, it works! Thanks a lot. :)

---

