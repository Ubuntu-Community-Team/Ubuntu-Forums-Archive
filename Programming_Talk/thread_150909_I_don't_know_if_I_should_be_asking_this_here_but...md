---
title: "I don't know if I should be asking this here but..."
date: 2006-03-26
forum: Programming Talk
---

### Post by DravenHavok on 2006-03-26
I'm messing around with programming, and I was wondering if I could post my code here. I just have a little problem that  I can't figure out. Let me tell you that I am NOT asking for help with my homework, I've had experiences like that so please don't accuse me of anything, with that in mind you don't have to reply. I was just looking for some help and hints. Since I'm liking this programing stuff. Well here's what I'm trying to do, something that will tell me if an input number is even or odd. Oh, and by the way, it's C language. Here's my code:

```

/*These are my comments! So the problem is that when I try to build 
it it gives me a syntax error were it says result = even( int); 
I don't unverstand why.*/


#include <stdio.h>

int even( int );

int main()
{
	int result;
	
	result = even( int );
	
	if result = 1
		printf("The number you entered is even./n");
	if result = 0
		printf("The number you entered is odd./n");
	return 0;
}

/*Function "even"*/

int even(int n)
{
	int number, solution;
	
	
	printf( "Please enter an integer./n");
	scanf( "%d", &number);
	
	solution = (number % 1);
	
	return solution;
}

```

Thanks for any help, and if this is unappropiate for this forum I apologize, and won't do it again. Thanks a lot!

---

### Post by IYY on 2006-03-27
Here's the problem:


> 	int result;
	
	result = even( int );

You can't be passing "int" to the function, you need an actual integer. For example, result = even (5). Or an integer variable like result = even (someinteger).

But it looks like this isn't even what you're trying to do. The way your function is set up, you aren't even using the integer argument (really, it shouldn't be a function at all but a method). So, in your function declaration, you should just have **int even ( void )**. And when you call it, don't pass any arguments.

---

### Post by thumper on 2006-03-27
number % 2 (modulus 2) will return 0 or 1 not "mod 1"

---

### Post by DravenHavok on 2006-03-27
Oh wow. I was off. Thank you so much, I think this programing thing is much more complicated when you don't remember your math. Thank you guys, I think I'm on the right track.

---

