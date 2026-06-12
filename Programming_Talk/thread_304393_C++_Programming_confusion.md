---
title: "C++ Programming confusion"
date: 2006-11-21
forum: Programming Talk
---

### Post by someonedumb on 2006-11-21
Why does this code give me an error ("The memory could not be "read")?

class cr{
public:
	int number;
};

void createcr(cr *n){
	n = new cr;
	n->number = 20;
}

void deletecr(cr *n){
	delete(n);
}

void main(){
	cr *t;
	createcr(t);
	deletecr(t);
}

Initializing *t to "NULL" makes the error go away, but I dont understand why that is... The crash occurs during the call to "deletecr(t)" so it shouldn't matte what "t" was initialized to because the initial value has been over written by the call to "createcr(t)"

---

### Post by slavik on 2006-11-21
class with only public can also be a struct (structs in C++ are exactly like classes but they are public by default).

---

### Post by po0f on 2006-11-21
someonedumb,

I've never seen the delete(blar) syntax before, and I don't know if it will work that way.  delete is a keyword, not a function.  Try changing it to just:
```
delete n;
```

---

### Post by someonedumb on 2006-11-21
Thanks for the replies :)

slavik - 
The error occurs wether I define cr as a class or struct.

po0f - 
Yes, I dont know why I started using parenthesis with the delete keyword. Its odd but has no effect on the quality of the code.

This is updated code based on your suggestions and the error still occurs. Feel free to try it in your own compilers.

struct cr{
	int number;
};

void createcr(cr *n){
	n = new cr;
	n->number = 20;
}

void deletecr(cr *n){
	delete n;
}

void main(){
	cr *t;
	createcr(t);
	deletecr(t);
}

---

### Post by hod139 on 2006-11-21
> **someonedumb said:**
> Why does this code give me an error ("The memory could not be "read")?

class cr{
public:
    int number;
};

void createcr(cr *n){
    n = new cr;
    n->number = 20;
}

void deletecr(cr *n){
    delete(n);
}

void main(){
    cr *t;
    createcr(t);
    deletecr(t);
}

Initializing *t to "NULL" makes the error go away, but I dont understand why that is... The crash occurs during the call to "deletecr(t)" so it shouldn't matte what "t" was initialized to because the initial value has been over written by the call to "createcr(t)"

I had to change void main() to int main() to make it valid C++ code, but otherwise it ran without an error.  May I also suggest that you pass the pointer by reference.  Below is my code with these changes.
```

class cr{
public:
  int number;
};

void createcr(cr * &n){
  n = new cr;
  n->number = 20;
}

void deletecr(cr * &n){
  delete(n);
}

int main(){
  cr *t;
  createcr(t);
  deletecr(t);
}

```

---

### Post by someonedumb on 2006-11-21
Thanks very much, that fixes it.
I have never seen a variable described by a pointer and a refrence in one line before: (cr * &n) :O

I realized what the error was in my code shortly after I posted my last reply, but couldn't resolve it.

To sum up the reason my original code had the error:

I was passing the pointer 't' to 'createcr' by value. The pointer 't' was copied to the variable 'n' defined in the 'createcr' argument list. Inside the 'createcr' function I allocate new memory and set 'n' to point to it, this does not cause 't' from main to change its value.

The error was then caused by trying to delete 't' when I never set it to point to anything.

---

### Post by hod139 on 2006-11-21
> **someonedumb said:**
> 
I have never seen a variable described by a pointer and a refrence in one line before: (cr * &n) :O

I realized what the error was in my code shortly after I posted my last reply, but couldn't resolve it.
I was passing the pointer 't' to 'createcr' by value. The pointer 't' was copied to the variable 'n' defined in the 'createcr' argument list. Inside the 'createcr' function I allocate new memory and set 'n' to point to it, this does not cause 't' from main to change its value.

The error was then caused by trying to delete 't' when I never set it to point to anything.

This is correct.  If you find the notation of passing a pointer by reference to be confusing, you can try passing a pointer to the pointer instead.  I however find this more confusing:
```

class cr{
public:
  int number;
};

void createcr(cr **n){
  (*n) = new cr;
  (*n)->number = 20;
}

void deletecr(cr **n){
  delete(*n);
}

int main(){
  cr *t;
  createcr(&t);
  deletecr(&t);
}

```

---

### Post by someonedumb on 2006-11-21
Thanks very much:)
I didn't mean to sound like I thought passing a pointer by reference was confusing, only that it was new to me. I'm actually really glad it came up so I could learn it.

Now I'm scratching my head over something else.

class big{
	double *d;
public:
	big(unsigned int size){
		d = new double[size];
	}
};

int main()
{
	cout << sizeof(double) << endl;
	big *x = new big(50000000);
	big *y = new big(50000000);
	big *z = new big(50000000);


	cout << "Done..." << endl;
	int b;
	cin >> b;

	delete x;
	delete y;
	delete z;

	cout << "Done again..." << endl;
	int c;
	cin >> c;

	return 0;
}

The purpose of the "done" lines are really just a lame attempt at pausing execution (you have to actually enter a number and press enter to get past the "pauses").

This code executes perfectly, it is possible to verify that the classes have been deleted etc.

My question is why doesn't task manager report the memory as having been freed up?

If you run this code this program will eat over a GB of your memory. Then if you enter a number and press enter to execute the 'delete' lines the memory (according to task manager) is not freed up. This occurs with classes or structs that dont contain dynamically allocated memory as well.

---

### Post by hod139 on 2006-11-21
When I run this code it only uses 836K of memory.  I'm guess g++ optimizes some stuff away??  What are you using to build your code?

---

### Post by someonedumb on 2006-11-21
Ugh, well I have one pretty big error in my explanation. The memory in this program does get freed up according to task manager when the large double arrays are not dynamically allocated within the class. This is the code:

class big{
	double a[50000000];
public:
	big(){
		a[0] = 10;
	}
};

int main()
{
	cout << sizeof(double) << endl;
	big *x = new big();
	big *y = new big();
	big *z = new big();


	cout << "Done..." << endl;
	int b;
	cin >> b;

	delete x;
	delete y;
	delete z;

	cout << "Done again..." << endl;
	int c;
	cin >> c;

	return 0;
}

So since its freed properly when the memory is not dynamically allocated the problem appears to be that I just need to add a destructor to the classes that use the dynamic allocation.

I am using Microsoft Visual Studio 6.0.

These large double arrays are going to take up alot of space, so I'm guessing the tool you're using to monitor memory is not reporting the dynamically allocated chunks. Unless it isn't allocated untill actually used?

---

### Post by someonedumb on 2006-11-21
How deep can a recursive function go before it returns prematurely?

---

### Post by hod139 on 2006-11-21
> **someonedumb said:**
> 
I am using Microsoft Visual Studio 6.0.

These large double arrays are going to take up alot of space, so I'm guessing the tool you're using to monitor memory is not reporting the dynamically allocated chunks. Unless it isn't allocated untill actually used?

First, can I ask what you are doing using Microsoft Visual Studio 6.0 and posting in a Linux forum!!! Just kidding, I don't really care, this could actually lead to some interesting comparisons between visual studio and g++ (like the fact that visual studio allows main to return a void in C++ and g++ is more standards compliant and does not).

I ran this code where you are allocating a ton of memory on the stack, but again, I'm only using 824K.  Even if I tell g++ to turn off all optimizations, I'm guessing it is being too smart and not allocating that memory.

---

### Post by hod139 on 2006-11-21
> **someonedumb said:**
> How deep can a recursive function go before it returns prematurely?
As far as I know, it will run until you run out of stack space, and faults.

---

### Post by someonedumb on 2006-11-22
> First, can I ask what you are doing using Microsoft Visual Studio 6.0 and posting in a Linux forum!!! Just kidding

Hehe! I didn't create this account out of the blue, I was on these boards quite a bit about a month ago when I was installing and configuring Ubuntu.

That is pretty interesting that it doesn't allocate the memory. I'll have to load up gcc sometime and try it out myself.

> this could actually lead to some interesting comparisons between visual studio and g++ 
Yes!
I was furious when I tried to use gcc after spending the time figuring out how to install it in Ubuntu.

I tried to write the simplest program and it gave me some incomprehenisble errors. Basically I could define a main() function and define some variables in it, but my first attempt at flow control (a simple for loop) made it explode, and I know the syntax was correct (from a Microsoft Visual C++ perspective; I did a direct copy and paste to verify that).

The error was something to do with mode 80 I think? I still have the log saved on my home computer, which I will have access to tomorrow.

Anyways, the good news is my main project is working now. I had some silly errors in my deletion algorithm that caused it to basically not do anything.

I really appriciate the advice, I learned some very usefull things :)

---

