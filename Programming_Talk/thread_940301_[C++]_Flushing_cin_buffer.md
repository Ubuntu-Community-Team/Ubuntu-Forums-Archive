---
title: "[C++] Flushing cin buffer"
date: 2008-10-06
forum: Programming Talk
---

### Post by babyhuey on 2008-10-06
What is the best way to flush cin after it fails?

For example:
[PHP]
int variable;
cin >> variable;
...
[/PHP]

In this case cin would create an infinite loop if the user entered a character; It fails until you get the buffer flushed.
I'm worried about someone entering other data types, not the range of integers.

---

### Post by cabalas on 2008-10-06
Checking out [http://cppreference.com/wiki/io/start](http://cppreference.com/wiki/io/start) should be helpful, now I haven't tested the following code so it may not work

[PHP]
int v = 0;

cin >> v; // I think you can also wrap this in a if statement

if(cin.fail())
  cin.flush()
[/PHP]

---

### Post by babyhuey on 2008-10-06
I don't think its that simple.(though it should be)
cin.flush() only flushes the failed state flag, and returns it to true.

Nevermind, I had cin.flush() and cin.clear() mixed up. 
cin.flush() doesn't seem to in iostream, I'm guessing its not part of standard c++

---

### Post by cabalas on 2008-10-06
> **babyhuey said:**
> I don't think its that simple.(though it should be)
cin.flush() only flushes the failed state flag, and returns it to true.

You are right, it's been a while since I wrote a commandline c++ app where I've needed to check user input.  Had a bit of downtime so I ran up a simple example which works for me:

[PHP]
#include <iostream>

int main() 
{
	int in = 0;
	do {
		std::cout << "Enter a number (10 to exit): ";
		std::cin >> in;
		
		if(std::cin.fail()) {
			in = 0;
			std::cin.clear();
			std::cin.get();
		}
	} while(in != 10);
	
	return 0;
}
[/PHP]

---

### Post by babyhuey on 2008-10-06
Thanks, that last one works. Though I swear I tried that almost exactly. :)

---

### Post by dwhitney67 on 2008-10-06
> **cabalas said:**
> You are right, it's been a while since I wrote a commandline c++ app where I've needed to check user input.  Had a bit of downtime so I ran up a simple example which works for me:

[PHP]
#include <iostream>

int main() 
{
	int in = 0;
	do {
		std::cout << "Enter a number (10 to exit): ";
		std::cin >> in;
		
		if(std::cin.fail()) {
			in = 0;
			std::cin.clear();
			std::cin.get();
		}
	} while(in != 10);
	
	return 0;
}
[/PHP]

The get() won't work unless the erroneous input is a single character.

The better option is to use ignore().

[PHP]
...
int number = 0;

while ( true )
{
  std::cout << "Enter a number: ";
  std::cin  >> number;

  if ( !std::cin.fail() )
    break;

  std::cin.clear();                 // clear the flags
  std::cin.ignore( 1024, '\n' );    // ignore at most 1024 chars until '\n' found
}
...
[/PHP]

---

### Post by babyhuey on 2008-10-06
> **dwhitney67 said:**
> The get() won't work unless the erroneous input is a single character.

The better option is to use ignore().

[PHP]
...
int number = 0;

while ( true )
{
  std::cout << "Enter a number: ";
  std::cin  >> number;

  if ( !std::cin.fail() )
    break;

  std::cin.clear();                 // clear the flags
  std::cin.ignore( 1024, '\n' );    // ignore at most 1024 chars until '\n' found
}
...
[/PHP]


Just found this out myself and came back here to post it :lolflag:

---

### Post by babyhuey on 2008-10-07
In an attempt to streamline this process I tried this:
[PHP]
int number = 0;
cin >> number;
while(cin.fail()){
  cin.clear();
  cin.ignore(1024, '\n');
  cin >> number;
}[/PHP]

I don't see why this would start an infinite loop. Any ideas?
I can't believe I'm having such trouble with the smallest tasks of the program :(

---

### Post by dwhitney67 on 2008-10-07
Your streamlined effort works for me; I cannot understand what problem you are having.  Would you care elaborate more?

I tried entering "abc" and the code worked as expected.  When I entered an integer, the while-loop terminated.

P.S.  Streamlining is wonderful, however in this case, it would be better to point out the operator's error and prompt them again as to what you want entered.  Hence the code snippet I submitted earlier is probably your best bet.

---

### Post by hod139 on 2008-10-07
Is this what you are looking for: [http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.3](http://www.parashift.com/c++-faq-lite/input-output.html#faq-15.3)

```

while(!(std::cin >> variable))
{
  std::cin.clear();
  std::cin.ignore(std::numeric_limits<streamsize>::max(),'\n');
}
```

---

### Post by gnusci on 2008-10-07
> **babyhuey said:**
> In an attempt to streamline this process I tried this:
[PHP]
int number = 0;
cin >> number;
while(cin.fail()){
  cin.clear();
  cin.ignore(1024, '\n');
  cin >> number;
}[/PHP]

I don't see why this would start an infinite loop. Any ideas?
I can't believe I'm having such trouble with the smallest tasks of the program :(

It works fine for me too... Which version of the compiler do you use?, post the output of this command:

**$ gcc --version**

---

### Post by babyhuey on 2008-10-07
> **dwhitney67 said:**
> Your streamlined effort works for me; I cannot understand what problem you are having.  Would you care elaborate more?

I tried entering "abc" and the code worked as expected.  When I entered an integer, the while-loop terminated.

P.S.  Streamlining is wonderful, however in this case, it would be better to point out the operator's error and prompt them again as to what you want entered.  Hence the code snippet I submitted earlier is probably your best bet.

Well, after coming back today it worked just fine. Apparently something was being wonky until I did a reboot. I ended up making a generic function sense it was going to be called many times.
[PHP]
void cinflush(){
  //made it a loop in case for some god awful reason the buffer
  //is over 1024bytes
  while(cin.fail()){  
    cin.clear();
    cin.ignore(1024, '\n');
    cout << "Input invalid, try again\n";
  }
}
[/PHP]

For example, call it by:
[PHP]
int number;
cout << "Enter a number";
cin >> number;
while(cin.fail()){
  cinflush();
  cin >> number;
}
[/PHP]

---

